---
ms.openlocfilehash: 5f990569ae4052377cba717b5526bb8ba51b8016
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636386"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Используйте класс [микседреалитиплайспаце](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) из Мртк для Unity и задайте **масштаб целевого объекта** **:** 

![Окно параметров МРТК](../../images/mrtk-target-scale.png)

МРТК должен автоматически управлять положением плайспаце и камеры, но рекомендуется дважды проверить следующее:

![МРТК плайспаце](../../images/mrtk-playspace.png)

1. На панели **Иерархия** разверните узел **микседреалитиплайспаце** GameObject и найдите основной дочерний объект **Camera** .
2. На панели **инспектора** найдите компонент **Преобразование** и измените его **Расположение** на **(X: 0, Y: 0, Z: 0)** .

# <a name="xr-sdk"></a>[Пакет SDK для XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Задайте режим источника отслеживания для [ксринпутсубсистем](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html). После получения подсистемы вызовите [трисеттраккингоригинмоде](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
```

И работать с [Ксрриг](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)Unity.

![XRная платформа в иерархии](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[Устаревший WSA](#tab/wsa)
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

Для работы с фиксированным **масштабированием** или **комнатным масштабированием** необходимо разместить содержимое относительно основания. Вы указываете на этаж пользователя с помощью **[пространственного этапа](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**, который представляет определенное пользователем происхождение на уровне пола и дополнительную границу комнаты, настраивается во время первого запуска.

Чтобы обеспечить работу Unity с своей мировой системой координат на уровне пола, можно установить и проверить, что Unity использует тип пространства отслеживания Румскале:

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

* Если Сеттраккингспацетипе возвращает значение true, Unity успешно переключил свою систему координат мира для мониторинга [промежуточного кадра ссылки](../../../../design/coordinate-systems.md#spatial-coordinate-systems).
* Если Сеттраккингспацетипе возвращает значение false, Unity не смог переключиться на промежуточный кадр ссылки, скорее всего потому, что пользователь не настроил этаж в своей среде. Хотя возвращаемое значение false не является распространенным, оно может произойти, если этап настраивается в другой комнате, и устройство перемещается в текущую комнату без настройки нового этапа пользователем.

После того как приложение успешно установит тип пространства отслеживания Румскале, на этаж будут отображаться содержимое, помещенное на плоскости y = 0. Источник 0, 0, 0 будет определять конкретное место в этаже, где пользователь стояли во время настройки комнаты, с параметром-Z, который соответствует направлению вперед во время установки.