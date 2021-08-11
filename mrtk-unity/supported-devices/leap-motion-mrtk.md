---
title: Использование Leap Motion
description: Документация по настройке LEAP
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, скачок,
ms.openlocfilehash: e675521a3a688bc0f9f8afdf1bdc01e583d0b47808d0aaff8b2eff263fce35bb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115222945"
---
# <a name="using-leap-motion"></a>Использование Leap Motion

Для использования этого поставщика данных требуется [контроллер движения LEAP](https://www.ultraleap.com/product/leap-motion-controller/) .

Поставщик данных о движении LEAP обеспечивает управляемую функцию отслеживания для VR и может быть полезна для быстрого создания прототипов в редакторе.  Поставщик данных может быть настроен на использование контроллера Motion LEAP, подключенного к гарнитуре или находящийся на рабочем столе.

![леапмотионинтрогиф](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

Этот поставщик можно использовать в редакторе и на устройстве на автономной платформе.  Его также можно использовать в редакторе на платформе UWP, но не в сборке UWP.

| Версия МРТК | Поддерживаемые версии модулей Unity для LEAP |
| --- | --- |
|2.6. x | 4.5.0, 4.5.1|
|2.7. x| 4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1, 4.8.0|


## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a>Отслеживание движения с помощью LEAP (by Ултралеап) в МРТК

1. Импорт модулей Unity МРТК и LEAP Motion
    - Установите последнюю версию [пакета SDK для LEAP](https://developer.leapmotion.com/releases/?category=orion) , если она еще не установлена
    - импортируйте объект **Microsoft. микседреалити. набор средств. Пакет Foundation** в проект Unity.
    - Скачайте и импортируйте в проект последнюю версию [модулей Unity Motion](https://developer.leapmotion.com/unity) .
        - Импортировать **основной** пакет только в пределах модулей Unity

1. Интеграция модулей Unity в LEAP с МРТК
    - после того как модули Unity будут находиться в проекте, перейдите в раздел **смешанная реальность набор средств**  >  **Leap motion**  >  **интеграция leap. модули Unity**
    > [!NOTE]
    > интеграция модулей Unity в мртк добавляет 10 определений сборок в проект и добавляет ссылки на **Microsoft. микседреалити. набор средств. Определение сборки providers. Леапмотион** . Убедитесь, что среда Visual Studio закрыта.

     ![леапмотионинтегратион](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. Добавление поставщика данных о движении LEAP
    - Создание новой сцены Unity
    - добавьте мртк в сцену, перейдя к " **смешанная реальность" набор средств**  >  **добавить в сцену и настроить**
    - Выберите в иерархии объект Game Микседреалититулкит и выберите **Копировать и настроить** , чтобы клонировать профиль смешанной реальности по умолчанию.

    ![леапмотионпрофилеклоне](../images/cross-platform/CloneProfile.png)

    - Выберите профиль **входной** конфигурации

    ![Входной профиль конфигурации 1](../images/cross-platform/InputConfigurationProfile.png)

    - Выберите **клон** во входном системном профиле, чтобы разрешить изменение.

    ![леапмотионинпутпрофилеклоне](../images/cross-platform/CloneInputSystemProfile.png)

    - Откройте раздел **поставщики входных данных** и выберите **Добавить поставщик данных** вверху. в конце списка будет добавлен новый поставщик данных.  откройте новый поставщик данных и задайте для него **тип** **Microsoft. микседреалити. набор средств. Леапмотион. Ввод > Леапмотиондевицеманажер**

    ![Добавление поставщика данных LEAP](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - Выберите **клон** , чтобы изменить параметры движения по умолчанию LEAP.

    ![леапдатапровидерпреклоне](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - Поставщик данных о движении LEAP содержит `LeapControllerOrientation` свойство, которое является расположением контроллера Motion LEAP. `LeapControllerOrientation.Headset` Указывает, что контроллер подключен к гарнитуре. `LeapControllerOrientation.Desk` Указывает, что контроллер размещается плоским на рабочем столе. По умолчанию устанавливается значение `LeapControllerOrientation.Headset` .
    - Ориентация каждого контроллера содержит свойства смещения:
      - Свойства смещения ориентации **гарнитуры** отражают свойства смещения в компоненте леапксрсервицепровидер.  `LeapVRDeviceOffsetMode`Имеет три параметра: Default, смещение и преобразование заголовка вручную.  Если используется режим смещения по умолчанию, то смещение не будет применяться к контроллеру движения LEAP.  Режим смещения Головков вручную позволяет изменять три свойства: `LeapVRDeviceOffsetY` , `LeapVRDeviceOffsetZ` и `LeapVRDeviceTiltX` .  Затем значения свойств смещения оси применяются к размещению контроллера по умолчанию.  Режим смещения преобразования содержит `LeapVRDeviceOrigin` свойство Transform, которое указывает новый источник для контроллера движения LEAP.
      - Ориентация на **Рабочий стол** содержит `LeapControllerOffset` свойство, определяющее положение точки привязки для стрелок на столе.  Смещение вычисляется относительно главной позиции камеры, а значение по умолчанию — (0,-0,2, 0,35), чтобы обеспечить отображение стрелок спереди и в представлении камеры.

        > [!NOTE]
        > Свойства смещения в профиле применяются один раз при запуске приложения.  Чтобы изменить значения во время выполнения, получите поставщик услуг LEAP Motion на основе диспетчер устройств Motion:
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - `EnterPinchDistance` и `ExitPinchDistance` — это пороговые значения расстояния для обнаружения жестов сжатия и воздушного касания.  Жест сжатия вычисляется путем измерения расстояния между кончиком указателя и кончиком пальца.  Чтобы вызвать событие при входе в систему, значение по умолчанию равно `EnterPinchDistance` 0,02.  Чтобы вызвать событие при входе в систему (выход из сжатия), расстояние по умолчанию между кончиком указателя по индексу и подсказкой Thumb будет 0,05.

    `LeapControllerOrientation`: Гарнитура (по умолчанию) |  `LeapControllerOrientation`: Рабочий стол
    :-------------------------:|:-------------------------:
    ![леафеадсетгиф](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![леапдескгиф](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![леафеадсетинспектор](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![леапдескинспектор](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. Тестирование поставщика данных движения LEAP
    - После добавления поставщика данных о движении LEAP в входной системный профиль нажмите кнопку Воспроизвести, переместите руку перед контроллером движения LEAP, и вы увидите представление руки.

1. Сборка проекта
    - выберите **файл > сборка Параметры**
    - При использовании поставщика данных о движении LEAP поддерживаются только автономные сборки.
    - инструкции по использованию гарнитуры Windows Mixed Reality для автономных сборок см. в статье [создание и развертывание мртк в вмр-гарнитурах (автономные)](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone).

## <a name="getting-the-hand-joints"></a>Получение соединений с рукой

Получение соединений с помощью поставщика данных о движении LEAP аналогично получению соединения типа "рука" с МРТКм.  Дополнительные сведения см. в разделе [Отслеживание вручную](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).

С помощью МРТК в сцене Unity и поставщика данных о движении LEAP, добавленного в качестве поставщика входных данных в входном системном профиле, создайте пустой объект Game и присоедините следующий пример скрипта.

Этот сценарий является простым примером того, как извлекать набор Объединенных соединений Palm при движении в LEAP.  Сфера соответствует левому углу, в то время как куб соответствует правой стороне.

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

## <a name="unity-editor-workflow-tip"></a>Совет по рабочему процессу редактора Unity

Для использования поставщика данных о движении LEAP не требуется гарнитура VR.  Изменения в приложении МРТК можно тестировать в редакторе с помощью LEAP без гарнитуры.

В редакторе будут отображаться стрелки движения, не подключенные к сети VR.  Если `LeapControllerOrientation` для задано значение **гарнитура**, то контроллеру Motion в LEAP должен быть назначена одна рука с камерой, направленной вперед.

> [!NOTE]
> Если камера перемещена с помощью ключей трассе в редакторе и `LeapControllerOrientation` является **гарнитурой**, руки не будут следовать за камерой. Руки будут перемещаться на камеру только в том случае, если телефонная гарнитура VR подключена, а `LeapControllerOrientation` задается **гарнитура**.  LEAP будет следовать за перемещением камеры в редакторе, если установлен в `LeapControllerOrientation` **рабочее** место.

## <a name="removing-leap-motion-from-the-project"></a>Удаление LEAP из Project

1. переход к   >  разным модулям Unity,**подвижным**  >   в смешанной реальности набор средств leap
    - разрешить обновление Unity в виде ссылок в **Microsoft. микседреалити. набор средств. На этом шаге изменяется файл providers. Леапмотион. асмдеф**
1. Закрыть Unity
1. закрыть Visual Studio, если он открыт
1. Откройте проводник и перейдите к корню проекта Unity МРТК.
    - Удаление каталога **унитипрожектнаме/Library**
    - Удалите каталог **унитипрожектнаме/Assets/plugins/леапмотион**
    - Удаление файла **унитипрожектнаме/Assets/plugins/леапмотион. meta**
1. Повторное открытие Unity

В Unity 2018,4 можно заметить, что ошибки по-прежнему остаются в консоли после удаления библиотеки и ресурсов ядра движения LEAP.
Если ошибки регистрируются после повторного открытия, перезапустите Unity еще раз.

## <a name="common-errors"></a>Общие ошибки

### <a name="leap-motion-has-not-integrated-with-mrtk"></a>LEAP не интегрирован с МРТК

Чтобы проверить, интегрированы ли модули Unity Motion с МРТК, выполните следующие действия.

- переход к **смешанной реальности набор средств > служебные программы > > Leap проверка состояния интеграции**
  - Откроется всплывающее окно с сообщением о том, интегрированы ли модули Unity для LEAP с МРТК.
- Если сообщение говорит о том, что ресурсы не были интегрированы:
  - Убедитесь, что модули Unity Motion находятся в проекте
  - Убедитесь, что добавленная версия поддерживается, см. таблицу в верхней части страницы для поддерживаемых версий.
  - испытайте **смешанную реальность набор средств > служебные программы > > leap интеграция модулей Unity для leap**

### <a name="copying-assembly-multiplayer-hlapi-failed"></a>Сбой при копировании многопользовательского ХЛАПИ сборки

При импорте ресурсов ядра Unity для работы с LEAP эта ошибка может быть записана в журнал:

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

**Решение**

- Краткосрочное решение — перезапустить Unity. Дополнительные сведения см. в описании [проблемы 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) .

## <a name="leap-motion-example-scene"></a>Сцена примера движения LEAP

В примере сцены используется профиль Дефаултлеапмотионконфигуратион и определяется, правильно ли настроен проект Unity для использования поставщика данных движения LEAP.

пример сцены содержится в **Microsoft. микседреалити. набор средств. Пример** пакета в **Мртк/examples/демонстрация/хандтраккинг/** каталог.  

## <a name="see-also"></a>См. также раздел

- [Поставщики входных данных](../features/input/input-providers.md)
- [Отслеживание рук](../features/input/hand-tracking.md)
