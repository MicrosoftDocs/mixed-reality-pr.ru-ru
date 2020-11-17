---
title: Взгляд в Unity
description: Взгляд — это основной способ, с помощью которого пользователи могут ориентироваться на голограммы, создаваемые приложением в смешанной реальности.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: взгляд на глаза, головной взгляд, Unity, голограмма, Смешанная реальность, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, МРТК, набор средств смешанной реальности
ms.openlocfilehash: 0c62de9cb1b7ea892831ea2cedbeb23be5ea7b37
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677513"
---
# <a name="head-gaze-in-unity"></a>Головной взгляд в Unity

[Взгляд](../../design/gaze-and-commit.md) — это основной способ, с помощью которого пользователи могут ориентироваться на [голограммы](../../discover/hologram.md) , создаваемые приложением в [смешанной реальности](../../discover/mixed-reality.md).


## <a name="implementing-head-gaze"></a>Реализация головного взгляда

По сути, [элемент "Head-взгляд](../../design/gaze-and-commit.md) " реализуется путем проецирования луча из заголовка пользователя, где находится гарнитура, в прямом направлении и определяет, что луч конфликтует с.
В Unity расположение и направление головного пользователя предоставляются с помощью основной [камеры](camera-in-unity.md)Unity, в частности [UnityEngine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [преобразование. Forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) и [UnityEngine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Disposition](https://docs.unity3d.com/ScriptReference/Transform-position.html).

Вызов функции [физик. райкаст](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) приводит к [райкассит](https://docs.unity3d.com/ScriptReference/RaycastHit.html) структуре, содержащей сведения о конфликте, включая трехмерную точку, в которой произошел конфликт, а другая GameObjectа, с которой был получен элемент head-взгляда.

### <a name="example-implement-head-gaze"></a>Пример: реализация Heading-взгляда

```cs
void Update()
{
       RaycastHit hitInfo;
       if (Physics.Raycast(
               Camera.main.transform.position,
               Camera.main.transform.forward,
               out hitInfo,
               20.0f,
               Physics.DefaultRaycastLayers))
       {
           // If the Raycast has succeeded and hit a hologram
           // hitInfo's point represents the position being gazed at
           // hitInfo's collider GameObject represents the hologram being gazed at
       }
}
```

### <a name="best-practices"></a>Рекомендации

Хотя в приведенном выше примере показано, как выполнить одно райкаст в цикле обновления, чтобы найти целевые точки пользователя, рекомендуется сделать это в одном объекте, управляющем Heading-взглядом, а не делать это в любом объекте, который потенциально заинтересован в объекте, газед в. Это позволяет приложению сохранять обработку, выполняя только один заголовок-взгляд, райкаст каждый кадр.

## <a name="visualizing-head-gaze"></a>Визуализация головного взгляда

Точно так же, как и на рабочем столе, где используется указатель мыши для назначения и взаимодействия с содержимым, следует реализовать [курсор](../../design/cursors.md) , представляющий голову пользователя. Это дает пользователю уверенность в том, с чем они взаимодействуют.

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a>Руководитель-взгляд в наборе средств Mixed Reality версии 2
Вы можете получить доступ к Head с помощью [диспетчера ввода](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) в мртк v2.

## <a name="next-development-checkpoint"></a>Следующий этап разработки

Если вы следуете изложенным нами этапам разработки для Unity, вы как раз прошли половину в изучении основных стандартных блоков MRTK. Отсюда вы можете перейти к следующему стандартному блоку:

> [!div class="nextstepaction"]
> [Жесты и контроллеры движений](gestures-and-motion-controllers-in-unity.md)

Или перейдите к возможностям и API платформы смешанной реальности:

> [!div class="nextstepaction"]
> [общие возможности](shared-experiences-in-unity.md);

Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#2-core-building-blocks).

## <a name="see-also"></a>См. также раздел
* [Камера](camera-in-unity.md)
* [Курсоры](../../design/cursors.md)
* [Направление головы и фиксация](../../design/gaze-and-commit.md)
