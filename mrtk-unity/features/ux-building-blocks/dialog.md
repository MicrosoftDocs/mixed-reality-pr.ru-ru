---
title: Диалог
description: Описание для элементов управления диалогового окна.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 5d63fcfe79a1c3b09c78f435cec3c2155b403795993f46628cf0f5743bfd42a7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203684"
---
# <a name="dialog"></a>Диалог

![Диалог](../images/dialog/MRTK_UX_Dialog_Main.png)

Элементы управления диалогового окна — это наложение пользовательского интерфейса, которое предоставляет контекстные сведения о приложении. Они часто требуют от пользователя совершения каких-либо действий. Диалоговые окна используются для уведомления пользователей о важной информации или запроса подтверждения либо дополнительных сведений перед совершением действия.

## <a name="example-scene"></a>Пример сцены

Примеры можно найти в сцене **диаложексампле** в разделе: [мртк/examples/Demo/UI/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/UX/Dialog) .

## <a name="how-to-use-dialog-control"></a>Как использовать элемент управления "диалоговое окно"

МРТК предоставляет три диалоговых Prefabs:

- DialogSmall_192x96. prefab
- DialogMedium_192x128. prefab
- DialogLarge_192x192. prefab

Используйте Dialog. Open (), чтобы открыть новое диалоговое окно. Укажите prefab диалогового окна, число кнопок, текст заголовка, текст сообщения, расстояние размещения (вблизи или далеко), дополнительные переменные). Диалоговое окно предоставляет параметры диалогового окна "подтверждение (одна кнопка)" и "Choice (две кнопки)".

```c#
public static Dialog Open(GameObject dialogPrefab, DialogButtonType buttons, string title, string message, bool placeForNearInteraction, System.Object variable = null)
```

### <a name="example-of-opening-a-large-dialog-with-a-single-ok-button-placed-at-far-interaction-range-gaze-hand-ray-motion-controller"></a>Пример открытия большого диалогового окна с одной кнопкой "ОК", размещенной в дальнем диапазоне (взгляд, рука-Ray, контроллер движения)

```c#
Dialog.Open(DialogPrefabLarge, DialogButtonType.OK, "Confirmation Dialog, Large, Far", "This is an example of a large dialog with only one button, placed at far interaction range", false);
```

### <a name="example-of-opening-a-small-dialog-containing-a-choice-message-for-the-user-placed-at-near-interaction-range-direct-hand-interaction"></a>Пример открытия небольшого диалогового окна, содержащего сообщение выбора для пользователя, расположенное в ближайшем диапазоне взаимодействия (непосредственное взаимодействие).

```c#
Dialog.Open(DialogPrefabSmall, DialogButtonType.Yes | DialogButtonType.No, "Confirmation Dialog, Small, Near", "This is an example of a small dialog with a choice message, placed at near interaction range", true);
```

Дополнительные сведения см `DialogExampleController.cs` . в разделе диаложексампле. Unity сцены.
