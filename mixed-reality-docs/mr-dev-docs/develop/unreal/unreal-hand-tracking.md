---
title: Отслеживание рук в Unreal
description: Объясняется, как использовать отслеживание вручную в нереальных
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, отслеживание, неreal, нереалное ядро 4, UE4, HoloLens, HoloLens 2, Смешанная реальность, разработка, функции, документация, руководства, голограммы, Разработка игр
ms.openlocfilehash: 5bc120f802c2160282befd1ce6cb8025be21cbaa
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91683084"
---
# <a name="hand-tracking-in-unreal"></a>Отслеживание рук в Unreal

## <a name="overview"></a>Обзор

Система отслеживания руки в качестве входных данных использует Палмс и пальцы человека. Вы можете получить расположение и поворот каждого пальца, всего карманного компьютера и даже руки, которые будут использоваться в коде. 

## <a name="hand-pose"></a>Рука

Рука руки позволяет отслеживанию руки и пальцы активного пользователя и использовать его в качестве входных данных, доступ к которым можно получить с помощью схем и C++. Дополнительные технические сведения можно найти в API [Windows. восприятие. People. хандпосе](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) . Нереалный API отправляет данные в виде системы координат с тактами, синхронизированными с нереальным механизмом.

### <a name="understanding-the-bone-hierarchy"></a>Основные сведения об иерархии костей

`EWMRHandKeypoint`Перечисление описывает иерархию костей руки. Вы можете найти все руки кэйпоинт, перечисленные в ваших чертежах:

![Кэйпоинт BP](images/hand-keypoint-bp.png)

Полное перечисление C++ показано ниже.
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

Числовые значения для каждого варианта перечисления можно найти в таблице [Windows. восприятие. People. ханджоинткинд](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) . На рисунке ниже показана вся схема оформления руки с соответствующими вариантами перечисления.

![Схема руки](../native/images/hand-skeleton.png)
 
### <a name="supporting-hand-tracking"></a>Поддержка отслеживания

Вы можете использовать отслеживание вручную в схемах, добавив **поддержку отслеживания вручную** для **отслеживания > Windows Mixed Reality** :

![BP для отслеживания](images/unreal/hand-tracking-bp.png)

Эта функция возвращает значение `true` , если отслеживание поддерживается на устройстве и `false` Если отслеживание недоступно.

![Поддерживает отправную очередь для отслеживания](images/unreal/supports-hand-tracking-bp.png)

C++: 

Добавьте `WindowsMixedRealityHandTrackingFunctionLibrary.h`.

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a>Отслеживание отслеживания
**Жесанджоинттрансформ** можно использовать для возврата пространственных данных из руки. Данные обновляются каждым кадром, но если вы находитесь внутри фрейма, возвращаемые значения кэшируются. В этой функции не рекомендуется использовать интенсивную логику для повышения производительности. 

![Преобразование «получение соединения с рукой»](images/unreal/get-hand-joint-transform.png)
 
C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

Разбиение параметров функции:

* **Рука** — левая или правая рука пользователя
* **Кэйпоинт** — кость руки. 
* **Transform** — координаты и ориентация базы данных-основания кости. Можно запросить основу следующей кости, чтобы получить данные преобразования для конца кости. Специальная кость TIP дает окончание дистал. 
* **Радиус** — радиус базовой части кости.
* **Возвращаемое значение** — true, если кость отслеживанием этого кадра, значение false, если кость не будет отслеживанием.

## <a name="hand-live-link-animation"></a>Анимация прямой связи
Руки, доступные для анимации, используют [подключаемый модуль динамической компоновки](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).

Если включены подключаемые модули Windows Mixed Reality и Live links: 
1. Выберите **окно > активная ссылка** , чтобы открыть окно редактора динамической связи. 
2. Щелкните **источник** и включите **источник отслеживания Windows Mixed Reality**

![Источник прямой связи](images/unreal/live-link-source.png)
 
После включения источника и открытия ресурса анимации раскройте раздел " **анимация** " на вкладке " **Предварительный просмотр** ". Дополнительные параметры см. в документации по нереальному каналу. так как подключаемый модуль находится в бета-версии, этот процесс может измениться позже.

![Динамическая анимация ссылки](images/unreal/live-link-animation.png)
 
Иерархия анимации руки такая же, как и в `EWMRHandKeypoint` . Анимацию можно перенацелить с помощью **виндовсмикседреалитихандтраккингливелинкремапассет** :

![Анимация прямой связи 2](images/unreal/live-link-animation2.png)
 
Он также может быть подклассом в редакторе:

![Сопоставление активных ссылок](images/unreal/live-link-remap.png)
 
## <a name="accessing-hand-mesh-data"></a>Доступ к данным сетки

![Сетка руки](images/unreal/hand-mesh.png)

Прежде чем можно будет получить доступ к данным сетки данных, необходимо:
- Выберите свой ресурс **арсессионконфиг** , разверните параметры **AR Settings-> мирового сопоставления** и установите флажок **создать данные сетки из отслеживающей геометрии** . 

Ниже приведены параметры сетки по умолчанию.

1.  Использование данных сетки для перекрытия
2.  Создать конфликт для данных сетки
3.  Создать сетку навигации для данных сетки
4.  Отображение данных сетки в каркасе — параметр отладки, показывающий созданную сетку

Эти значения параметров используются в качестве сетки пространственного сопоставления и по умолчанию для сетки. Их можно изменить в любой момент в проекте или коде для любой сетки.

### <a name="c-api-reference"></a>Справочник по API C++ 
Используется `EEARObjectClassification` для поиска значений сетки в объектах, доступных для наблюдения.
```cpp
enum class EARObjectClassification : uint8
{
    // Other types 
    HandMesh,
};
```

Следующие делегаты вызываются, когда система обнаруживает любой отслеживающий объект, включая сетку типа "рука". 

```cpp
class FARSupportInterface 
{
    public:
    // Other params 
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

Убедитесь, что обработчики делегатов следуют сигнатуре функции ниже:

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

Доступ к данным сетки можно получить с помощью  `UARTrackedGeometry::GetUnderlyingMesh` :

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```


### <a name="blueprint-api-reference"></a>Справочник по API-интерфейсам схем

Для работы с сетчатыми сетками в схемах:
1. Добавление компонента **артраккабленотифи** в проект схемы

![Уведомление Артраккабле](images/unreal/ar-trackable-notify.png)
 
2. Перейдите на панель **сведений** и разверните раздел **события** . 

![Артраккабле уведомление 2](images/unreal/ar-trackable-notify2.png)
 
3. Перезаписать для добавления, обновления или удаления отслеживаний геометрии со следующими узлами в графе событий:

![Уведомление Артраккабле](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a>Лучи с рукой

Можно использовать входной луч в качестве указывающего устройства как в C++, так и в чертежах, которые предоставляют API [Windows. UI. input. spatial. спатиалпоинтеринтерактионсаурцепосе](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) .

Важно упомянуть, что поскольку результаты всех функций изменяют каждый кадр, все они становятся вызываемыми. Дополнительные сведения о чистом и нечистом или вызываемых функциях см. в статье GUID пользователя в [функциях](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure) .

Чтобы использовать лучи в схемах, выполните поиск любых действий в **Windows Mixed Reality ХМД** :

![BP](images/unreal/hand-rays-bp.png)
 
Чтобы получить доступ к ним в C++, включите `WindowsMixedRealityFunctionLibrary.h` в начало файла вызывающего кода.

### <a name="enum"></a>Перечисление
Кроме того, у вас есть доступ к входным вариантам в **ехмдинпутконтроллербуттонс** , которые можно использовать в схемах:

![Кнопки контроллера ввода](images/unreal/input-controller-buttons.png)

Для доступа в C++ используйте `EHMDInputControllerButtons` Класс Enum:
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

Ниже приведена разбивка двух применимых вариантов перечисления.
* **SELECT** — пользователь активировал событие SELECT. 
    * Событие можно активировать в HoloLens 2, выполнив касание, взгляните и зафиксировать, или выполнив команду "Select" с включенным [голосовым входом](unreal-voice-input.md) . 
* Пользовательское событие **, активируемое с** учетом продачи. 
    * Это событие может быть активировано в HoloLens 2 путем закрытия пальцев пользователя на голограмме. 

Вы можете получить доступ к состоянию отслеживания сетки руки в C++ с помощью `EHMDTrackingStatus` перечисления, показанного ниже:

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

Ниже приведена разбивка двух применимых вариантов перечисления.
* **Ноттраккед** — рука не отображается
* С **отслеживанием** — рука полностью отслеживание

### <a name="struct"></a>Структура
Структура Поинтерпосеинфо может предоставить сведения о следующих данных:
* **Источник** — источник руки
* **Направление** — направление руки
* **Вверх** — вверх в виде вектора руки
* **Orientation** — ориентация кватерниона 
* **Состояние отслеживания** — текущее состояние отслеживания

Доступ к нему можно получить с помощью схем, как показано ниже:

![BP, сведения о указателе](images/unreal/pointer-pose-info-bp.png)

Или с + +:

```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```

### <a name="functions"></a>Функции

Все перечисленные ниже функции можно вызывать для каждого кадра, что позволяет выполнять непрерывный мониторинг. 

1. **Получить сведения о выведении указателя** возвращает полные сведения о направлении ладони в текущем кадре. 

Схем

![Получить сведения о указателе](images/unreal/get-pointer-pose-info.png)

C++: 
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. Если рука проблюдается в текущем кадре, **будет** возвращено значение true.

Схем

![Есть BP](images/unreal/is-grasped-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
 
3. При **нажатии кнопки выбрать** возвращается значение true, если пользователь активировал выбор в текущем кадре.

Схем

![Выбрана нажатая нажимаемая BP](images/unreal/is-select-pressed-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. Нажата **кнопка "** возвращает значение true", если событие или кнопка активированы в текущем кадре.

Схем

![Нажата кнопка BP](images/unreal/is-button-clicked-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. **Получение состояния отслеживания контроллера** возвращает состояние отслеживания в текущем кадре.

Схем

![Получить состояние отслежения контроллера](images/unreal/get-controller-tracking-status-bp.png)

C++:
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```

## <a name="gestures"></a>Жесты

Hololens 2 может отслеживать пространственные жесты, что означает возможность захвата этих жестов в качестве входных данных. Дополнительные сведения о жестах можно найти в документе [об использовании HoloLens 2](https://docs.microsoft.com/hololens/hololens2-basic-usage) .

Функцию схемы можно найти в разделе **пространственный ввод Windows Mixed Reality** , а функция C++ — путем добавления `WindowsMixedRealitySpatialInputFunctionLibrary.h` в файл вызывающего кода.

![Жесты записи](images/unreal/capture-gestures.png)

### <a name="enum"></a>Перечисление
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
Схем 

![Тип жеста](images/unreal/gesture-type.png)

C++:
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a>Функция
Включить и отключить захват жестов можно с помощью `CaptureGestures` функции. Когда включенный жест запускает входные события, функция возвращает значение, `true` Если захват жеста завершается удачно, и `false` при наличии ошибки.

Схем

![Точка применения жестов захвата](images/unreal/capture-gestures-bp.png)

C++:
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```

Ниже приведены ключевые события, которые можно найти в чертежах и C++: ключевые события. ![](images/unreal/key-events.png)

![Ключевые события 2](images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```

## <a name="next-development-checkpoint"></a>Контрольная точка следующей разработки

Если вы подготовились к нереальному пути к контрольной точке разработки, мы собрались в исследовании стандартных блоков МРТК Core. Отсюда можно перейти к следующему стандартному блоку: 

> [!div class="nextstepaction"]
> [Локальные пространственные привязки](unreal-spatial-anchors.md)

Или перейти к возможностям платформы смешанной реальности и API-интерфейсам:

> [!div class="nextstepaction"]
> [Камера HoloLens](unreal-hololens-camera.md)

Вы всегда можете вернуться к [нереальным контрольным точкам разработки](unreal-development-overview.md#2-core-building-blocks) в любое время.