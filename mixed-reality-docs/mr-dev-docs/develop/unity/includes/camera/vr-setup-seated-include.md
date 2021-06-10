---
ms.openlocfilehash: 3bffb5db8f4a36d04c2b408c939cbd2010a7def7
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748495"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Используйте класс [микседреалитиплайспаце](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) из Мртк для Unity и задайте для **целевого шкалы** значение **"** подключено":

![Окно параметров МРТК](../../images/mrtk-target-scale.png)

МРТК должен автоматически управлять положением плайспаце и камеры, но рекомендуется дважды проверить следующее:

![МРТК плайспаце](../../images/mrtk-playspace.png)

1. На панели **Иерархия** разверните узел **микседреалитиплайспаце** GameObject и найдите основной дочерний объект **Camera** .
2. На панели **инспектора** найдите компонент **Преобразование** и измените его **Расположение** на **(X: 0, Y: 0, Z: 0)** .

# <a name="xr-sdk"></a>[Пакет SDK для XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Задайте режим источника отслеживания для [ксринпутсубсистем](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html). После получения подсистемы вызовите [трисеттраккингоригинмоде](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
```

И работать с [Ксрриг](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)Unity.

![XRная платформа в иерархии](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[Устаревшая версия WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. В разделе " **другие параметры** " окна " **Параметры проигрывателя магазина Windows** "
2. Выберите **Windows Mixed Reality** в качестве устройства, которое может быть указано как **Windows holographic** в более ранних версиях Unity.
3. Выбрать **поддерживаемую виртуальную реальность**

Так как основной объект Camera автоматически помечается как камера, Unity перемещает все движения и перевод.

>[!NOTE]
>Эти параметры должны применяться к камере в каждой сцене приложения.
>
>По умолчанию при создании новой сцены в Unity она будет содержать главную GameObject камеры в иерархии, которая включает компонент камеры, но не имеет правильно примененных параметров.

**Пространство имен:** *UnityEngine. XR*<br>
**Тип:** *ксрдевице*

Чтобы создать **интерфейс с горизонтальной** **ориентацией** или с возможностями масштабирования, необходимо задать Unity как стационарный тип пространства отслеживания. Стационарное пространство отслеживания. устанавливает мировую систему координат Unity для отслеживания [стационарной рамки ссылки](../../../../design/coordinate-systems.md#spatial-coordinate-systems). В режиме нестационарного отслеживания содержимое, помещенное в редактор непосредственно перед расположением по умолчанию камеры (переадресация — Z), будет отображаться перед пользователем при запуске приложения.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**Пространство имен:** *UnityEngine. XR*<br>
**Тип:** *инпуттраккинг*

Для чистой **ориентации** , такой как видео-средство просмотра 360 (если позиционированные головные обновления насмарку иллюзию), можно установить [XR. Инпуттраккинг. Дисаблепоситионалтраккинг](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) имеет значение true:

```cs
InputTracking.disablePositionalTracking = true;
```

Для **работы с возможностями масштабирования**, чтобы пользователь мог позже изменить центр исходного места, можно вызвать [XR. Метод Инпуттраккинг. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) :

```cs
InputTracking.Recenter();
```

Если вы создаете [опыт](../../../../design/coordinate-systems.md)в области, вы можете изменить центр по всему миру в текущей позиции головного пользователя, вызвав **[XR. Метод Инпуттраккинг. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** .