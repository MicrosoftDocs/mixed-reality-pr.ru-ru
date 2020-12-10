---
title: Взгляд в Unity
description: Взгляд — это основной способ, с помощью которого пользователи могут ориентироваться на голограммы, создаваемые приложением в смешанной реальности.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: взгляд на глаза, головной взгляд, Unity, голограмма, Смешанная реальность, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, МРТК, набор средств смешанной реальности
ms.openlocfilehash: ca33fef5a5a761df83ed7991b366cf711a5db224
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010365"
---
# <a name="head-gaze-in-unity"></a>Головной взгляд в Unity

[Взгляд](../../design/gaze-and-commit.md) — это основной способ, с помощью которого пользователи могут ориентироваться на [голограммы](../../discover/hologram.md) , создаваемые приложением в [смешанной реальности](../../discover/mixed-reality.md).

## <a name="implementing-head-gaze"></a>Реализация головного взгляда

По сути, вы определяете [головное взгляд](../../design/gaze-and-commit.md) , выполняя проекцию луча вперед от гарнитуры пользователя, чтобы узнать, что он касается. В Unity расположение и направление головного пользователя предоставляются через [камеру](camera-in-unity.md), в частности [UnityEngine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [преобразование. Forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) и [UnityEngine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Disposition](https://docs.unity3d.com/ScriptReference/Transform-position.html).

Вызов функции [физик. райкаст](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) дает вам [райкассит](https://docs.unity3d.com/ScriptReference/RaycastHit.html) , содержащий сведения о конфликте, включая трехмерную точку конфликта, а другой GameObject — попадание в голову.

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

Хотя в приведенном выше примере в цикле обновления создается один райкаст, чтобы найти целевые точки пользователя, мы рекомендуем использовать один объект для управления всеми процессами головного взгляда. Объединение логики с помощью Head-взгляда позволит сохранить ценную вычислительную мощность приложения и ограничить райкастинг на один кадр.

## <a name="visualizing-head-gaze"></a>Визуализация головного взгляда

Как и в случае с указателем мыши на компьютере, необходимо реализовать [курсор](../../design/cursors.md) , представляющий голову пользователя. Знание содержимого, на которое нацелен пользователь, повышает уверенность в том, с чем они взаимодействуют.

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a>Руководитель-взгляд в наборе средств Mixed Reality 
Вы можете получить доступ к Head с помощью [диспетчера ввода](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) в мртк.

## <a name="next-development-checkpoint"></a>Следующий этап разработки

Если вы пойдете из пути разработки Unity, мы собрались, что вы в состоянии изучить стандартные блоки МРТК Core. Отсюда можно перейти к следующему стандартному блоку:

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
