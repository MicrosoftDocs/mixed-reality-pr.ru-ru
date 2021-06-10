---
ms.openlocfilehash: 6e751f5376110ddc6ae92c75b4182fba8240a356
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748500"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Следуйте этому пошаговому [руководству, чтобы](../../tutorials/mr-learning-base-01.md) добавить и автоматически настроить набор средств смешанной реальности в проекте Unity. Кроме того, можно напрямую работать с классом [микседреалитиплайспаце](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) из Мртк для Unity и задать для **целевого масштаба** значение **World**:

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
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

[Арсессион](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) можно использовать для приложений HoloLens, которые работают лучше с привязками и ARKit/Аркоре.

![Сеанс AR в иерархии](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> Для сеанса AR и связанных компонентов требуется установка AR Foundation.

Можно также применить изменения камеры вручную, не используя Арсессион:

1. На панели **Иерархия** выберите **Главная камера** .
1. На панели **инспектора** найдите компонент **Преобразование** и измените его **Расположение** на **(X: 0, Y: 0, Z: 0)** .

   ![Камера на панели инспектора в Unity](../../images/maincamera-350px.png)  
   *Камера на панели инспектора в Unity*

1. Добавление **траккедпоседривер** к **основной камере**

# <a name="legacy-wsa"></a>[Устаревшая версия WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. На панели **Иерархия** выберите **Главная камера** .
1. На панели **инспектора** найдите компонент **Преобразование** и измените его **Расположение** на **(X: 0, Y: 0, Z: 0)** .

   ![Камера на панели инспектора в Unity](../../images/maincamera-350px.png)  
   *Камера на панели инспектора в Unity*

1. В разделе " **другие параметры** " окна " **Параметры проигрывателя магазина Windows** "
1. Выберите **Windows Mixed Reality** в качестве устройства, которое может быть указано как **Windows holographic** в более ранних версиях Unity.
1. Выбрать **поддерживаемую виртуальную реальность**

Так как основной объект Camera автоматически помечается как камера, Unity перемещает все движения и перевод.

>[!NOTE]
>Эти параметры должны применяться к камере в каждой сцене приложения.
>
>По умолчанию при создании новой сцены в Unity она будет содержать главную GameObject камеры в иерархии, которая включает компонент камеры, но может не иметь правильно примененных параметров.