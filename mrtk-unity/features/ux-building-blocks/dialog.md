---
title: Диалог
description: Описание для элементов управления диалогового окна.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 729c3f6a6b9bc63a498c5d76205a0730f52c678a
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489194"
---
# <a name="dialog"></a><span data-ttu-id="4dc5b-104">Диалог</span><span class="sxs-lookup"><span data-stu-id="4dc5b-104">Dialog</span></span>

![Диалог](../images/dialog/MRTK_UX_Dialog_Main.png)

<span data-ttu-id="4dc5b-106">Элементы управления диалогового окна — это наложение пользовательского интерфейса, которое предоставляет контекстные сведения о приложении.</span><span class="sxs-lookup"><span data-stu-id="4dc5b-106">Dialog controls are UI overlays that provide contextual app information.</span></span> <span data-ttu-id="4dc5b-107">Они часто требуют от пользователя совершения каких-либо действий.</span><span class="sxs-lookup"><span data-stu-id="4dc5b-107">They often request some kind of action from the user.</span></span> <span data-ttu-id="4dc5b-108">Диалоговые окна используются для уведомления пользователей о важной информации или запроса подтверждения либо дополнительных сведений перед совершением действия.</span><span class="sxs-lookup"><span data-stu-id="4dc5b-108">Use dialogs to notify users of important information or to request confirmation or additional info before an action can be completed.</span></span>

## <a name="example-scene"></a><span data-ttu-id="4dc5b-109">Пример сцены</span><span class="sxs-lookup"><span data-stu-id="4dc5b-109">Example scene</span></span>

<span data-ttu-id="4dc5b-110">Примеры можно найти в сцене **диаложексампле** в разделе: [мртк/examples/Demo/UI/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/UX/Dialog) .</span><span class="sxs-lookup"><span data-stu-id="4dc5b-110">You can find examples in the **DialogExample** scene under: [MRTK/Examples/Demo/UX/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/UX/Dialog)</span></span>

## <a name="how-to-use-dialog-control"></a><span data-ttu-id="4dc5b-111">Как использовать элемент управления "диалоговое окно"</span><span class="sxs-lookup"><span data-stu-id="4dc5b-111">How to use Dialog control</span></span>

<span data-ttu-id="4dc5b-112">МРТК предоставляет три диалоговых Prefabs:</span><span class="sxs-lookup"><span data-stu-id="4dc5b-112">MRTK provides three Dialog prefabs:</span></span>

- <span data-ttu-id="4dc5b-113">DialogSmall_192x96. prefab</span><span class="sxs-lookup"><span data-stu-id="4dc5b-113">DialogSmall_192x96.prefab</span></span>
- <span data-ttu-id="4dc5b-114">DialogMedium_192x128. prefab</span><span class="sxs-lookup"><span data-stu-id="4dc5b-114">DialogMedium_192x128.prefab</span></span>
- <span data-ttu-id="4dc5b-115">DialogLarge_192x192. prefab</span><span class="sxs-lookup"><span data-stu-id="4dc5b-115">DialogLarge_192x192.prefab</span></span>

<span data-ttu-id="4dc5b-116">Используйте Dialog. Open (), чтобы открыть новое диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="4dc5b-116">Use Dialog.Open() to open a new dialog.</span></span> <span data-ttu-id="4dc5b-117">Укажите prefab диалогового окна, число кнопок, текст заголовка, текст сообщения, расстояние размещения (вблизи или далеко), дополнительные переменные).</span><span class="sxs-lookup"><span data-stu-id="4dc5b-117">Specify the dialog prefab, number of buttons, title text, message text, placement distance(near or far), additional variables).</span></span> <span data-ttu-id="4dc5b-118">Диалоговое окно предоставляет параметры диалогового окна "подтверждение (одна кнопка)" и "Choice (две кнопки)".</span><span class="sxs-lookup"><span data-stu-id="4dc5b-118">Dialog provides 'Confirmation(single button)' and 'Choice(two-buttons)' dialog options.</span></span>

```c#
public static Dialog Open(GameObject dialogPrefab, DialogButtonType buttons, string title, string message, bool placeForNearInteraction, System.Object variable = null)
```

### <a name="example-of-opening-a-large-dialog-with-a-single-ok-button-placed-at-far-interaction-range-gaze-hand-ray-motion-controller"></a><span data-ttu-id="4dc5b-119">Пример открытия большого диалогового окна с одной кнопкой "ОК", размещенной в дальнем диапазоне (взгляд, рука-Ray, контроллер движения)</span><span class="sxs-lookup"><span data-stu-id="4dc5b-119">Example of opening a Large dialog with a single 'OK' button, placed at far interaction range (gaze, hand ray, motion controller)</span></span>

```c#
Dialog.Open(DialogPrefabLarge, DialogButtonType.OK, "Confirmation Dialog, Large, Far", "This is an example of a large dialog with only one button, placed at far interaction range", false);
```

### <a name="example-of-opening-a-small-dialog-containing-a-choice-message-for-the-user-placed-at-near-interaction-range-direct-hand-interaction"></a><span data-ttu-id="4dc5b-120">Пример открытия небольшого диалогового окна, содержащего сообщение выбора для пользователя, расположенное в ближайшем диапазоне взаимодействия (непосредственное взаимодействие).</span><span class="sxs-lookup"><span data-stu-id="4dc5b-120">Example of opening a Small dialog containing a choice message for the user, placed at near interaction range (direct hand interaction)</span></span>

```c#
Dialog.Open(DialogPrefabSmall, DialogButtonType.Yes | DialogButtonType.No, "Confirmation Dialog, Small, Near", "This is an example of a small dialog with a choice message, placed at near interaction range", true);
```

<span data-ttu-id="4dc5b-121">Дополнительные сведения см `DialogExampleController.cs` . в разделе диаложексампле. Unity сцены.</span><span class="sxs-lookup"><span data-stu-id="4dc5b-121">For more details, please see `DialogExampleController.cs` in DialogExample.unity scene.</span></span>
