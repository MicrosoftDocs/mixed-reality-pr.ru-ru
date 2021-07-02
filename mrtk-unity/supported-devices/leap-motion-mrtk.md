---
title: Использование Leap Motion
description: Документация по настройке LEAP
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, скачок,
ms.openlocfilehash: 3ddf039f8409022d8aa2e425c46cd4d47ede16a0
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176516"
---
# <a name="using-leap-motion"></a><span data-ttu-id="8e872-104">Использование Leap Motion</span><span class="sxs-lookup"><span data-stu-id="8e872-104">Using Leap Motion</span></span>

<span data-ttu-id="8e872-105">Для использования этого поставщика данных требуется [контроллер движения LEAP](https://www.ultraleap.com/product/leap-motion-controller/) .</span><span class="sxs-lookup"><span data-stu-id="8e872-105">A [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) is required to use this data provider.</span></span>

<span data-ttu-id="8e872-106">Поставщик данных о движении LEAP обеспечивает управляемую функцию отслеживания для VR и может быть полезна для быстрого создания прототипов в редакторе.</span><span class="sxs-lookup"><span data-stu-id="8e872-106">The Leap Motion Data Provider enables articulated hand tracking for VR and could be useful for rapid prototyping in the editor.</span></span>  <span data-ttu-id="8e872-107">Поставщик данных может быть настроен на использование контроллера Motion LEAP, подключенного к гарнитуре или находящийся на рабочем столе.</span><span class="sxs-lookup"><span data-stu-id="8e872-107">The data provider can be configured to use the Leap Motion Controller mounted on a headset or placed on a desk face up.</span></span>

![леапмотионинтрогиф](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

<span data-ttu-id="8e872-109">Этот поставщик можно использовать в редакторе и на устройстве на автономной платформе.</span><span class="sxs-lookup"><span data-stu-id="8e872-109">This provider can be used in editor and on device while on the Standalone platform.</span></span>  <span data-ttu-id="8e872-110">Его также можно использовать в редакторе на платформе UWP, но не в сборке UWP.</span><span class="sxs-lookup"><span data-stu-id="8e872-110">It can also be used in editor while on the UWP platform but NOT in a UWP build.</span></span>

| <span data-ttu-id="8e872-111">Версия МРТК</span><span class="sxs-lookup"><span data-stu-id="8e872-111">MRTK Version</span></span> | <span data-ttu-id="8e872-112">Поддерживаемые версии модулей Unity для LEAP</span><span class="sxs-lookup"><span data-stu-id="8e872-112">Leap Motion Unity Modules Versions Supported</span></span> |
| --- | --- |
|<span data-ttu-id="8e872-113">2.6. x</span><span class="sxs-lookup"><span data-stu-id="8e872-113">2.6.x</span></span> | <span data-ttu-id="8e872-114">4.5.0, 4.5.1</span><span class="sxs-lookup"><span data-stu-id="8e872-114">4.5.0, 4.5.1</span></span>|
|<span data-ttu-id="8e872-115">2.7. x</span><span class="sxs-lookup"><span data-stu-id="8e872-115">2.7.x</span></span>| <span data-ttu-id="8e872-116">4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1, 4.8.0</span><span class="sxs-lookup"><span data-stu-id="8e872-116">4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1, 4.8.0</span></span>|


## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="8e872-117">Отслеживание движения с помощью LEAP (by Ултралеап) в МРТК</span><span class="sxs-lookup"><span data-stu-id="8e872-117">Using Leap Motion (by Ultraleap) hand tracking in MRTK</span></span>

1. <span data-ttu-id="8e872-118">Импорт модулей Unity МРТК и LEAP Motion</span><span class="sxs-lookup"><span data-stu-id="8e872-118">Importing MRTK and the Leap Motion Unity Modules</span></span>
    - <span data-ttu-id="8e872-119">Установите последнюю версию [пакета SDK для LEAP](https://developer.leapmotion.com/releases/?category=orion) , если она еще не установлена</span><span class="sxs-lookup"><span data-stu-id="8e872-119">Install the latest [Leap Motion SDK](https://developer.leapmotion.com/releases/?category=orion) if it is not already installed</span></span>
    - <span data-ttu-id="8e872-120">импортируйте объект **Microsoft. микседреалити. набор средств. Пакет Foundation** в проект Unity.</span><span class="sxs-lookup"><span data-stu-id="8e872-120">Import the **Microsoft.MixedReality.Toolkit.Foundation** package into the Unity project.</span></span>
    - <span data-ttu-id="8e872-121">Скачайте и импортируйте в проект последнюю версию [модулей Unity Motion](https://developer.leapmotion.com/unity) .</span><span class="sxs-lookup"><span data-stu-id="8e872-121">Download and import the latest version of the [Leap Motion Unity Modules](https://developer.leapmotion.com/unity) into the project</span></span>
        - <span data-ttu-id="8e872-122">Импортировать **основной** пакет только в пределах модулей Unity</span><span class="sxs-lookup"><span data-stu-id="8e872-122">Only import the **Core** package within the Unity Modules</span></span>

1. <span data-ttu-id="8e872-123">Интеграция модулей Unity в LEAP с МРТК</span><span class="sxs-lookup"><span data-stu-id="8e872-123">Integrate the Leap Motion Unity Modules with MRTK</span></span>
    - <span data-ttu-id="8e872-124">после того как модули Unity будут находиться в проекте, перейдите в раздел **смешанная реальность набор средств**  >  **Leap motion**  >  **интеграция leap. модули Unity**</span><span class="sxs-lookup"><span data-stu-id="8e872-124">After the Unity Modules are in the project, navigate to **Mixed Reality Toolkit** > **Leap Motion** > **Integrate Leap Motion Unity Modules**</span></span>
    > [!NOTE]
    > <span data-ttu-id="8e872-125">интеграция модулей Unity в мртк добавляет 10 определений сборок в проект и добавляет ссылки на **Microsoft. микседреалити. набор средств. Определение сборки providers. Леапмотион** .</span><span class="sxs-lookup"><span data-stu-id="8e872-125">Integrating the Unity Modules to MRTK adds 10 assembly definitions to the project and adds references to the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion** assembly definition.</span></span> <span data-ttu-id="8e872-126">Убедитесь, что среда Visual Studio закрыта.</span><span class="sxs-lookup"><span data-stu-id="8e872-126">Make sure Visual Studio is closed.</span></span>

     ![леапмотионинтегратион](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. <span data-ttu-id="8e872-128">Добавление поставщика данных о движении LEAP</span><span class="sxs-lookup"><span data-stu-id="8e872-128">Adding the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="8e872-129">Создание новой сцены Unity</span><span class="sxs-lookup"><span data-stu-id="8e872-129">Create a new Unity scene</span></span>
    - <span data-ttu-id="8e872-130">добавьте мртк в сцену, перейдя к " **смешанная реальность" набор средств**  >  **добавить в сцену и настроить**</span><span class="sxs-lookup"><span data-stu-id="8e872-130">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    - <span data-ttu-id="8e872-131">Выберите в иерархии объект Game Микседреалититулкит и выберите **Копировать и настроить** , чтобы клонировать профиль смешанной реальности по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8e872-131">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

    ![леапмотионпрофилеклоне](../images/cross-platform/CloneProfile.png)

    - <span data-ttu-id="8e872-133">Выберите профиль **входной** конфигурации</span><span class="sxs-lookup"><span data-stu-id="8e872-133">Select the **Input** Configuration Profile</span></span>

    ![Входной профиль конфигурации 1](../images/cross-platform/InputConfigurationProfile.png)

    - <span data-ttu-id="8e872-135">Выберите **клон** во входном системном профиле, чтобы разрешить изменение.</span><span class="sxs-lookup"><span data-stu-id="8e872-135">Select **Clone** in the input system profile to enable modification.</span></span>

    ![леапмотионинпутпрофилеклоне](../images/cross-platform/CloneInputSystemProfile.png)

    - <span data-ttu-id="8e872-137">Откройте раздел **поставщики входных данных** и выберите **Добавить поставщик данных** вверху. в конце списка будет добавлен новый поставщик данных.</span><span class="sxs-lookup"><span data-stu-id="8e872-137">Open the **Input Data Providers** section, select **Add Data Provider** at the top, a new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="8e872-138">откройте новый поставщик данных и задайте для него **тип** **Microsoft. микседреалити. набор средств. Леапмотион. Ввод > Леапмотиондевицеманажер**</span><span class="sxs-lookup"><span data-stu-id="8e872-138">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager**</span></span>

    ![Добавление поставщика данных LEAP](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - <span data-ttu-id="8e872-140">Выберите **клон** , чтобы изменить параметры движения по умолчанию LEAP.</span><span class="sxs-lookup"><span data-stu-id="8e872-140">Select **Clone** to change the default Leap Motion settings.</span></span>

    ![леапдатапровидерпреклоне](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - <span data-ttu-id="8e872-142">Поставщик данных о движении LEAP содержит `LeapControllerOrientation` свойство, которое является расположением контроллера Motion LEAP.</span><span class="sxs-lookup"><span data-stu-id="8e872-142">The Leap Motion Data Provider contains the `LeapControllerOrientation` property which is the location of the Leap Motion Controller.</span></span> <span data-ttu-id="8e872-143">`LeapControllerOrientation.Headset` Указывает, что контроллер подключен к гарнитуре.</span><span class="sxs-lookup"><span data-stu-id="8e872-143">`LeapControllerOrientation.Headset` indicates the controller is mounted on a headset.</span></span> <span data-ttu-id="8e872-144">`LeapControllerOrientation.Desk` Указывает, что контроллер размещается плоским на рабочем столе.</span><span class="sxs-lookup"><span data-stu-id="8e872-144">`LeapControllerOrientation.Desk` indicates the controller is placed flat on desk.</span></span> <span data-ttu-id="8e872-145">По умолчанию устанавливается значение `LeapControllerOrientation.Headset` .</span><span class="sxs-lookup"><span data-stu-id="8e872-145">The default value is set to `LeapControllerOrientation.Headset`.</span></span>
    - <span data-ttu-id="8e872-146">Ориентация каждого контроллера содержит свойства смещения:</span><span class="sxs-lookup"><span data-stu-id="8e872-146">Each controller orientation contains offset properties:</span></span>
      - <span data-ttu-id="8e872-147">Свойства смещения ориентации **гарнитуры** отражают свойства смещения в компоненте леапксрсервицепровидер.</span><span class="sxs-lookup"><span data-stu-id="8e872-147">The **Headset** orientation offset properties mirror the offset properties in the LeapXRServiceProvider component.</span></span>  <span data-ttu-id="8e872-148">`LeapVRDeviceOffsetMode`Имеет три параметра: Default, смещение и преобразование заголовка вручную.</span><span class="sxs-lookup"><span data-stu-id="8e872-148">The `LeapVRDeviceOffsetMode` has three options: Default, Manual Head Offset and Transform.</span></span>  <span data-ttu-id="8e872-149">Если используется режим смещения по умолчанию, то смещение не будет применяться к контроллеру движения LEAP.</span><span class="sxs-lookup"><span data-stu-id="8e872-149">If the offset mode is Default, then an offset will not be applied to the Leap Motion Controller.</span></span>  <span data-ttu-id="8e872-150">Режим смещения Головков вручную позволяет изменять три свойства: `LeapVRDeviceOffsetY` , `LeapVRDeviceOffsetZ` и `LeapVRDeviceTiltX` .</span><span class="sxs-lookup"><span data-stu-id="8e872-150">The Manual Head Offset mode allows for the modification of three properties: `LeapVRDeviceOffsetY`, `LeapVRDeviceOffsetZ` and `LeapVRDeviceTiltX`.</span></span>  <span data-ttu-id="8e872-151">Затем значения свойств смещения оси применяются к размещению контроллера по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8e872-151">The axis offset property values are then applied to default controller placement.</span></span>  <span data-ttu-id="8e872-152">Режим смещения преобразования содержит `LeapVRDeviceOrigin` свойство Transform, которое указывает новый источник для контроллера движения LEAP.</span><span class="sxs-lookup"><span data-stu-id="8e872-152">The Transform offset mode contains the `LeapVRDeviceOrigin` Transform property which specifies a new origin for the Leap Motion Controller.</span></span>
      - <span data-ttu-id="8e872-153">Ориентация на **Рабочий стол** содержит `LeapControllerOffset` свойство, определяющее положение точки привязки для стрелок на столе.</span><span class="sxs-lookup"><span data-stu-id="8e872-153">The **Desk** orientation contains the `LeapControllerOffset` property which defines the anchor position of the desk leap hands.</span></span>  <span data-ttu-id="8e872-154">Смещение вычисляется относительно главной позиции камеры, а значение по умолчанию — (0,-0,2, 0,35), чтобы обеспечить отображение стрелок спереди и в представлении камеры.</span><span class="sxs-lookup"><span data-stu-id="8e872-154">The offset is calculated relative to the main camera position and the default value is (0,-0.2, 0.35) to make sure the hands appear in front and in view of the camera.</span></span>

        > [!NOTE]
        > <span data-ttu-id="8e872-155">Свойства смещения в профиле применяются один раз при запуске приложения.</span><span class="sxs-lookup"><span data-stu-id="8e872-155">The offset properties in the profile are applied once when the application starts.</span></span>  <span data-ttu-id="8e872-156">Чтобы изменить значения во время выполнения, получите поставщик услуг LEAP Motion на основе диспетчер устройств Motion:</span><span class="sxs-lookup"><span data-stu-id="8e872-156">To modify the values during runtime, get the Leap Motion Service Provider from the Leap Motion Device Manager:</span></span>
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - <span data-ttu-id="8e872-157">`EnterPinchDistance` и `ExitPinchDistance` — это пороговые значения расстояния для обнаружения жестов сжатия и воздушного касания.</span><span class="sxs-lookup"><span data-stu-id="8e872-157">`EnterPinchDistance` and `ExitPinchDistance` are the distance thresholds for pinch/air tap gesture detection.</span></span>  <span data-ttu-id="8e872-158">Жест сжатия вычисляется путем измерения расстояния между кончиком указателя и кончиком пальца.</span><span class="sxs-lookup"><span data-stu-id="8e872-158">The pinch gesture is calculated by measuring the distance between the index finger tip and the thumb tip.</span></span>  <span data-ttu-id="8e872-159">Чтобы вызвать событие при входе в систему, значение по умолчанию равно `EnterPinchDistance` 0,02.</span><span class="sxs-lookup"><span data-stu-id="8e872-159">To raise an on input down event, the default `EnterPinchDistance` is set to 0.02.</span></span>  <span data-ttu-id="8e872-160">Чтобы вызвать событие при входе в систему (выход из сжатия), расстояние по умолчанию между кончиком указателя по индексу и подсказкой Thumb будет 0,05.</span><span class="sxs-lookup"><span data-stu-id="8e872-160">To raise an on input up event (exiting the pinch), the default distance between the index finger tip and the thumb tip is 0.05.</span></span>

    <span data-ttu-id="8e872-161">`LeapControllerOrientation`: Гарнитура (по умолчанию)</span><span class="sxs-lookup"><span data-stu-id="8e872-161">`LeapControllerOrientation`: Headset (Default)</span></span> |  <span data-ttu-id="8e872-162">`LeapControllerOrientation`: Рабочий стол</span><span class="sxs-lookup"><span data-stu-id="8e872-162">`LeapControllerOrientation`: Desk</span></span>
    :-------------------------:|:-------------------------:
    ![леафеадсетгиф](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![леапдескгиф](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![леафеадсетинспектор](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![леапдескинспектор](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. <span data-ttu-id="8e872-167">Тестирование поставщика данных движения LEAP</span><span class="sxs-lookup"><span data-stu-id="8e872-167">Testing the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="8e872-168">После добавления поставщика данных о движении LEAP в входной системный профиль нажмите кнопку Воспроизвести, переместите руку перед контроллером движения LEAP, и вы увидите представление руки.</span><span class="sxs-lookup"><span data-stu-id="8e872-168">After Leap Motion Data Provider has been added to the input system profile, press play, move your hand in front of the Leap Motion Controller and you should see the joint representation of the hand.</span></span>

1. <span data-ttu-id="8e872-169">Сборка проекта</span><span class="sxs-lookup"><span data-stu-id="8e872-169">Building your project</span></span>
    - <span data-ttu-id="8e872-170">выберите **файл > сборка Параметры**</span><span class="sxs-lookup"><span data-stu-id="8e872-170">Navigate to **File > Build Settings**</span></span>
    - <span data-ttu-id="8e872-171">При использовании поставщика данных о движении LEAP поддерживаются только автономные сборки.</span><span class="sxs-lookup"><span data-stu-id="8e872-171">Only Standalone builds are supported if using the Leap Motion Data Provider.</span></span>
    - <span data-ttu-id="8e872-172">инструкции по использованию гарнитуры Windows Mixed Reality для автономных сборок см. в статье [создание и развертывание мртк в вмр-гарнитурах (автономные)](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone).</span><span class="sxs-lookup"><span data-stu-id="8e872-172">For instructions on how to use a Windows Mixed Reality headset for Standalone builds, see [Building and deploying MRTK to WMR Headsets (Standalone)](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone).</span></span>

## <a name="getting-the-hand-joints"></a><span data-ttu-id="8e872-173">Получение соединений с рукой</span><span class="sxs-lookup"><span data-stu-id="8e872-173">Getting the hand joints</span></span>

<span data-ttu-id="8e872-174">Получение соединений с помощью поставщика данных о движении LEAP аналогично получению соединения типа "рука" с МРТКм.</span><span class="sxs-lookup"><span data-stu-id="8e872-174">Getting joints using the Leap Motion Data Provider is identical to hand joint retrieval for an MRTK Articulated Hand.</span></span>  <span data-ttu-id="8e872-175">Дополнительные сведения см. в разделе [Отслеживание вручную](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span><span class="sxs-lookup"><span data-stu-id="8e872-175">For more information, see [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span></span>

<span data-ttu-id="8e872-176">С помощью МРТК в сцене Unity и поставщика данных о движении LEAP, добавленного в качестве поставщика входных данных в входном системном профиле, создайте пустой объект Game и присоедините следующий пример скрипта.</span><span class="sxs-lookup"><span data-stu-id="8e872-176">With MRTK in a unity scene and the Leap Motion Data Provider added as an Input Data Provider in the Input System profile, create an empty game object and attach the following example script.</span></span>

<span data-ttu-id="8e872-177">Этот сценарий является простым примером того, как извлекать набор Объединенных соединений Palm при движении в LEAP.</span><span class="sxs-lookup"><span data-stu-id="8e872-177">This script is a simple example of how to retrieve the pose of the palm joint in a Leap Motion Hand.</span></span>  <span data-ttu-id="8e872-178">Сфера соответствует левому углу, в то время как куб соответствует правой стороне.</span><span class="sxs-lookup"><span data-stu-id="8e872-178">A sphere follows the left Leap hand while a cube follows the right Leap hand.</span></span>

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

## <a name="unity-editor-workflow-tip"></a><span data-ttu-id="8e872-179">Совет по рабочему процессу редактора Unity</span><span class="sxs-lookup"><span data-stu-id="8e872-179">Unity editor workflow tip</span></span>

<span data-ttu-id="8e872-180">Для использования поставщика данных о движении LEAP не требуется гарнитура VR.</span><span class="sxs-lookup"><span data-stu-id="8e872-180">Using the Leap Motion Data Provider does not require a VR headset.</span></span>  <span data-ttu-id="8e872-181">Изменения в приложении МРТК можно тестировать в редакторе с помощью LEAP без гарнитуры.</span><span class="sxs-lookup"><span data-stu-id="8e872-181">Changes to an MRTK app can be tested in the editor with the Leap hands without a headset.</span></span>

<span data-ttu-id="8e872-182">В редакторе будут отображаться стрелки движения, не подключенные к сети VR.</span><span class="sxs-lookup"><span data-stu-id="8e872-182">The Leap Motion Hands will show up in the editor, without a VR headset plugged in.</span></span>  <span data-ttu-id="8e872-183">Если `LeapControllerOrientation` для задано значение **гарнитура**, то контроллеру Motion в LEAP должен быть назначена одна рука с камерой, направленной вперед.</span><span class="sxs-lookup"><span data-stu-id="8e872-183">If the `LeapControllerOrientation` is set to **Headset**, then the Leap Motion controller will need to be held up by one hand with the camera facing forward.</span></span>

> [!NOTE]
> <span data-ttu-id="8e872-184">Если камера перемещена с помощью ключей трассе в редакторе и `LeapControllerOrientation` является **гарнитурой**, руки не будут следовать за камерой.</span><span class="sxs-lookup"><span data-stu-id="8e872-184">If the camera is moved using WASD keys in the editor and the `LeapControllerOrientation` is **Headset**, the hands will not follow the camera.</span></span> <span data-ttu-id="8e872-185">Руки будут перемещаться на камеру только в том случае, если телефонная гарнитура VR подключена, а `LeapControllerOrientation` задается **гарнитура**.</span><span class="sxs-lookup"><span data-stu-id="8e872-185">The hands will only follow camera movement if a VR headset is plugged in while the `LeapControllerOrientation` is set **Headset**.</span></span>  <span data-ttu-id="8e872-186">LEAP будет следовать за перемещением камеры в редакторе, если установлен в `LeapControllerOrientation` **рабочее** место.</span><span class="sxs-lookup"><span data-stu-id="8e872-186">The Leap hands will follow the camera movement in the editor if the `LeapControllerOrientation` is set to **Desk**.</span></span>

## <a name="removing-leap-motion-from-the-project"></a><span data-ttu-id="8e872-187">Удаление LEAP из Project</span><span class="sxs-lookup"><span data-stu-id="8e872-187">Removing Leap Motion from the Project</span></span>

1. <span data-ttu-id="8e872-188">переход к   >  разным модулям Unity,**подвижным**  >   в смешанной реальности набор средств leap</span><span class="sxs-lookup"><span data-stu-id="8e872-188">Navigate to the **Mixed Reality Toolkit** > **Leap Motion** > **Separate Leap Motion Unity Modules**</span></span>
    - <span data-ttu-id="8e872-189">разрешить обновление Unity в виде ссылок в **Microsoft. микседреалити. набор средств. На этом шаге изменяется файл providers. Леапмотион. асмдеф**</span><span class="sxs-lookup"><span data-stu-id="8e872-189">Let Unity refresh as references in the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** file are modified in this step</span></span>
1. <span data-ttu-id="8e872-190">Закрыть Unity</span><span class="sxs-lookup"><span data-stu-id="8e872-190">Close Unity</span></span>
1. <span data-ttu-id="8e872-191">закрыть Visual Studio, если он открыт</span><span class="sxs-lookup"><span data-stu-id="8e872-191">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="8e872-192">Откройте проводник и перейдите к корню проекта Unity МРТК.</span><span class="sxs-lookup"><span data-stu-id="8e872-192">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
    - <span data-ttu-id="8e872-193">Удаление каталога **унитипрожектнаме/Library**</span><span class="sxs-lookup"><span data-stu-id="8e872-193">Delete the **UnityProjectName/Library** directory</span></span>
    - <span data-ttu-id="8e872-194">Удалите каталог **унитипрожектнаме/Assets/plugins/леапмотион**</span><span class="sxs-lookup"><span data-stu-id="8e872-194">Delete the **UnityProjectName/Assets/Plugins/LeapMotion** directory</span></span>
    - <span data-ttu-id="8e872-195">Удаление файла **унитипрожектнаме/Assets/plugins/леапмотион. meta**</span><span class="sxs-lookup"><span data-stu-id="8e872-195">Delete the **UnityProjectName/Assets/Plugins/LeapMotion.meta** file</span></span>
1. <span data-ttu-id="8e872-196">Повторное открытие Unity</span><span class="sxs-lookup"><span data-stu-id="8e872-196">Reopen Unity</span></span>

<span data-ttu-id="8e872-197">В Unity 2018,4 можно заметить, что ошибки по-прежнему остаются в консоли после удаления библиотеки и ресурсов ядра движения LEAP.</span><span class="sxs-lookup"><span data-stu-id="8e872-197">In Unity 2018.4, you might notice that errors still remain in the console after deleting the Library and the Leap Motion Core Assets.</span></span>
<span data-ttu-id="8e872-198">Если ошибки регистрируются после повторного открытия, перезапустите Unity еще раз.</span><span class="sxs-lookup"><span data-stu-id="8e872-198">If errors are logged after reopening, restart Unity again.</span></span>

## <a name="common-errors"></a><span data-ttu-id="8e872-199">Общие ошибки</span><span class="sxs-lookup"><span data-stu-id="8e872-199">Common Errors</span></span>

### <a name="leap-motion-has-not-integrated-with-mrtk"></a><span data-ttu-id="8e872-200">LEAP не интегрирован с МРТК</span><span class="sxs-lookup"><span data-stu-id="8e872-200">Leap Motion has not integrated with MRTK</span></span>

<span data-ttu-id="8e872-201">Чтобы проверить, интегрированы ли модули Unity Motion с МРТК, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="8e872-201">To test if the Leap Motion Unity Modules have integrated with MRTK:</span></span>

- <span data-ttu-id="8e872-202">переход к **смешанной реальности набор средств > служебные программы > > Leap проверка состояния интеграции**</span><span class="sxs-lookup"><span data-stu-id="8e872-202">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status**</span></span>
  - <span data-ttu-id="8e872-203">Откроется всплывающее окно с сообщением о том, интегрированы ли модули Unity для LEAP с МРТК.</span><span class="sxs-lookup"><span data-stu-id="8e872-203">This will display a pop up window with a message about whether or not the Leap Motion Unity Modules have integrated with MRTK.</span></span>
- <span data-ttu-id="8e872-204">Если сообщение говорит о том, что ресурсы не были интегрированы:</span><span class="sxs-lookup"><span data-stu-id="8e872-204">If the message says that the assets have not been integrated:</span></span>
  - <span data-ttu-id="8e872-205">Убедитесь, что модули Unity Motion находятся в проекте</span><span class="sxs-lookup"><span data-stu-id="8e872-205">Make sure the Leap Motion Unity Modules are in the project</span></span>
  - <span data-ttu-id="8e872-206">Убедитесь, что добавленная версия поддерживается, см. таблицу в верхней части страницы для поддерживаемых версий.</span><span class="sxs-lookup"><span data-stu-id="8e872-206">Make sure that the version added is supported, see the table at the top of the page for versions supported.</span></span>
  - <span data-ttu-id="8e872-207">испытайте **смешанную реальность набор средств > служебные программы > > leap интеграция модулей Unity для leap**</span><span class="sxs-lookup"><span data-stu-id="8e872-207">Try **Mixed Reality Toolkit > Utilities > Leap Motion > Integrate Leap Motion Unity Modules**</span></span>

### <a name="copying-assembly-multiplayer-hlapi-failed"></a><span data-ttu-id="8e872-208">Сбой при копировании многопользовательского ХЛАПИ сборки</span><span class="sxs-lookup"><span data-stu-id="8e872-208">Copying assembly Multiplayer HLAPI failed</span></span>

<span data-ttu-id="8e872-209">При импорте ресурсов ядра Unity для работы с LEAP эта ошибка может быть записана в журнал:</span><span class="sxs-lookup"><span data-stu-id="8e872-209">On import of the Leap Motion Unity Core Assets this error might be logged:</span></span>

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

<span data-ttu-id="8e872-210">**Решение**</span><span class="sxs-lookup"><span data-stu-id="8e872-210">**Solution**</span></span>

- <span data-ttu-id="8e872-211">Краткосрочное решение — перезапустить Unity.</span><span class="sxs-lookup"><span data-stu-id="8e872-211">A short term solution is to restart Unity.</span></span> <span data-ttu-id="8e872-212">Дополнительные сведения см. в описании [проблемы 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) .</span><span class="sxs-lookup"><span data-stu-id="8e872-212">See [Issue 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) for more information.</span></span>

## <a name="leap-motion-example-scene"></a><span data-ttu-id="8e872-213">Сцена примера движения LEAP</span><span class="sxs-lookup"><span data-stu-id="8e872-213">Leap Motion Example Scene</span></span>

<span data-ttu-id="8e872-214">В примере сцены используется профиль Дефаултлеапмотионконфигуратион и определяется, правильно ли настроен проект Unity для использования поставщика данных движения LEAP.</span><span class="sxs-lookup"><span data-stu-id="8e872-214">The example scene uses the DefaultLeapMotionConfiguration profile and determines if the Unity project has been configured correctly to use the Leap Motion Data Provider.</span></span>

<span data-ttu-id="8e872-215">пример сцены содержится в **Microsoft. микседреалити. набор средств. Пример** пакета в **Мртк/examples/демонстрация/хандтраккинг/** каталог.</span><span class="sxs-lookup"><span data-stu-id="8e872-215">The example scene is contained in the **Microsoft.MixedReality.Toolkit.Examples** package in the **MRTK/Examples/Demos/HandTracking/** directory.</span></span>  

## <a name="see-also"></a><span data-ttu-id="8e872-216">См. также:</span><span class="sxs-lookup"><span data-stu-id="8e872-216">See also</span></span>

- [<span data-ttu-id="8e872-217">Поставщики входных данных</span><span class="sxs-lookup"><span data-stu-id="8e872-217">Input Providers</span></span>](../features/input/input-providers.md)
- [<span data-ttu-id="8e872-218">Отслеживание вручную</span><span class="sxs-lookup"><span data-stu-id="8e872-218">Hand Tracking</span></span>](../features/input/hand-tracking.md)
