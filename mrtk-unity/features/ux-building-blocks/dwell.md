---
title: Вдаваясь
description: Взаимодействие вдаваясь
author: cre8ivepark
ms.author: dongpark
ms.date: 05/20/2021
keywords: Вдаваясь, Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 18e69f001c8989234d1b75fb713796f079cacbdf
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647864"
---
# <a name="dwell"></a><span data-ttu-id="8b752-104">Вдаваясь</span><span class="sxs-lookup"><span data-stu-id="8b752-104">Dwell</span></span>

![Вдаваясь Hero](../images/dwell/MRTK_UX_Dwell.png)

<span data-ttu-id="8b752-106">Head-взгляд и вдаваясь являются великолепной в ситуациях, когда руки человека заняты другими задачами.</span><span class="sxs-lookup"><span data-stu-id="8b752-106">Head-gaze and dwell are great in scenarios where a person's hands are busy with other tasks.</span></span> <span data-ttu-id="8b752-107">Эта функция также полезна, если речь не 100% надежности или доступности в связи с ограничениями на окружающую среду или социальные сети.</span><span class="sxs-lookup"><span data-stu-id="8b752-107">The feature is also useful when voice isn't 100% reliable or available because of environmental or social constraints.</span></span>
<span data-ttu-id="8b752-108">В примерах вдаваясь МРТК демонстрируются различные типы компонентов пользовательского интерфейса с настраиваемым временем отклика и визуальным отзывом.</span><span class="sxs-lookup"><span data-stu-id="8b752-108">MRTK's dwell examples demonstrate different types of UI components with configurable response time and visual feedback.</span></span>

<span data-ttu-id="8b752-109">Рекомендации по проектированию см. на странице с [рекомендациями Head и вдаваясь](/windows/mixed-reality/design/gaze-and-dwell-head) .</span><span class="sxs-lookup"><span data-stu-id="8b752-109">Please see [Head-gaze and dwell guideline](/windows/mixed-reality/design/gaze-and-dwell-head) page for the design recommendations.</span></span>

## <a name="dwell-scripts"></a><span data-ttu-id="8b752-110">Вдаваясь сценарии</span><span class="sxs-lookup"><span data-stu-id="8b752-110">Dwell scripts</span></span>

- <span data-ttu-id="8b752-111">**Двеллхандлер**: добавляет модальность вдаваясь к целевому объекту пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="8b752-111">**DwellHandler**: Adds a dwell modality to the UI target.</span></span>
- <span data-ttu-id="8b752-112">**Двеллстатетипе**: состояния обработчика вдаваясь.</span><span class="sxs-lookup"><span data-stu-id="8b752-112">**DwellStateType**: The states of the dwell handler.</span></span>
- <span data-ttu-id="8b752-113">**Двеллунитевент**: событие Unity для события вдаваясь.</span><span class="sxs-lookup"><span data-stu-id="8b752-113">**DwellUnityEvent**: Unity event for a dwell event.</span></span> <span data-ttu-id="8b752-114">Содержит ссылку на указатель.</span><span class="sxs-lookup"><span data-stu-id="8b752-114">Contains the pointer reference.</span></span>
- <span data-ttu-id="8b752-115">**Баседвеллпрессаблебуттон. CS** : скрипт, который запускает событие OnClick () в `Interactable` PressableButtonHoloLens2 Prefabs.</span><span class="sxs-lookup"><span data-stu-id="8b752-115">**BaseDwellPressableButton.cs** : A script that triggers OnClick() event in `Interactable` of PressableButtonHoloLens2 prefabs.</span></span>
- <span data-ttu-id="8b752-116">**Тоггледвеллпрессаблебуттон. CS** : этот скрипт изменяет `_BorderWidth` свойство объекта, `dwellVisualImage` который использует шейдер мртк Standard.</span><span class="sxs-lookup"><span data-stu-id="8b752-116">**ToggleDwellPressableButton.cs** : This script modifies `_BorderWidth` property of the `dwellVisualImage` which is using MRTK Standard Shader.</span></span>

## <a name="dwell-profiles"></a><span data-ttu-id="8b752-117">Профили вдаваясь</span><span class="sxs-lookup"><span data-stu-id="8b752-117">Dwell profiles</span></span>
<span data-ttu-id="8b752-118">Профили вдаваясь используются **обработчиком вдаваясь** для настройки различных порогов.</span><span class="sxs-lookup"><span data-stu-id="8b752-118">Dwell profiles are used by the **Dwell Handler** to configure the various thresholds.</span></span>
- <span data-ttu-id="8b752-119">**Буттондвеллпрофиле. актив**</span><span class="sxs-lookup"><span data-stu-id="8b752-119">**ButtonDwellProfile.asset**</span></span>
- <span data-ttu-id="8b752-120">**Инстанддвеллпрофиле. актив**</span><span class="sxs-lookup"><span data-stu-id="8b752-120">**InstandDwellProfile.asset**</span></span>
- <span data-ttu-id="8b752-121">**Двеллпрофилевисдекай. актив**</span><span class="sxs-lookup"><span data-stu-id="8b752-121">**DwellProfileWithDecay.asset**</span></span>

## <a name="prefabs"></a><span data-ttu-id="8b752-122">Prefabs</span><span class="sxs-lookup"><span data-stu-id="8b752-122">Prefabs</span></span>

<span data-ttu-id="8b752-123">Эти Prefabs являются вариантами кнопки Prefabs в стиле HoloLens 2, которые имеют дополнительные компоненты для поддержки взаимодействий вдаваясь.</span><span class="sxs-lookup"><span data-stu-id="8b752-123">These prefabs are variants of the HoloLens 2 style pressable button prefabs that have additional components to support dwell interactions.</span></span>

- <span data-ttu-id="8b752-124">**PressableButtonHoloLens2_Dwell. prefab**</span><span class="sxs-lookup"><span data-stu-id="8b752-124">**PressableButtonHoloLens2_Dwell.prefab**</span></span>
- <span data-ttu-id="8b752-125">**PressableButtonHoloLens2_32x96_Dwell. prefab**</span><span class="sxs-lookup"><span data-stu-id="8b752-125">**PressableButtonHoloLens2_32x96_Dwell.prefab**</span></span>
- <span data-ttu-id="8b752-126">**PressableButtonHoloLens2ToggleDwell. prefab**</span><span class="sxs-lookup"><span data-stu-id="8b752-126">**PressableButtonHoloLens2ToggleDwell.prefab**</span></span>
- <span data-ttu-id="8b752-127">**PressableButtonHoloLens2Toggle_32x96_Dwell. prefab**</span><span class="sxs-lookup"><span data-stu-id="8b752-127">**PressableButtonHoloLens2Toggle_32x96_Dwell.prefab**</span></span>

<span data-ttu-id="8b752-128">Эти Prefabs имеют дополнительный компонент **куаддвеллвисуал** для визуализации состояния ввода вдаваясь.</span><span class="sxs-lookup"><span data-stu-id="8b752-128">These prefabs have an additional backplate component **QuadDwellVisual** to visualize the dwell input state.</span></span> <span data-ttu-id="8b752-129">У него есть **холографикбаккплатедвеллвисуал** материалов.</span><span class="sxs-lookup"><span data-stu-id="8b752-129">It has **HolographicBackPlateDwellVisual.mat** material assigned.</span></span> <span data-ttu-id="8b752-130">**Тоггледвеллпрессаблебуттон. CS** обновляет свойство **_BorderWidth** стандартного шейдера мртк для визуализации входных данных вдаваясь.</span><span class="sxs-lookup"><span data-stu-id="8b752-130">**ToggleDwellPressableButton.cs** updates the **_BorderWidth** property of MRTK Standard shader to visualize the dwell input.</span></span>

<img src="../images/dwell/MRTK_UX_Dwell_Prefabs_Structure.png" alt="Dwell prefabs structure" width="550px">
<img src="../images/dwell/MRTK_UX_Dwell_Prefabs.png" alt="Dwell prefabs" width="350px">

## <a name="example-scene"></a><span data-ttu-id="8b752-131">Пример сцены</span><span class="sxs-lookup"><span data-stu-id="8b752-131">Example scene</span></span>

<span data-ttu-id="8b752-132">Примеры можно найти в `DwellExample` сцене.</span><span class="sxs-lookup"><span data-stu-id="8b752-132">You can find examples in the `DwellExample` scene.</span></span> <span data-ttu-id="8b752-133">В примере сцены показаны примеры пользовательского интерфейса объемные и примеры пользовательского интерфейса Unity.</span><span class="sxs-lookup"><span data-stu-id="8b752-133">The example scene shows both volumetric UI examples and Unity UI examples.</span></span>

<img src="../images/dwell/MRTK_UX_Dwell_Examples.png" alt="Near Menu Example">

## <a name="see-also"></a><span data-ttu-id="8b752-134">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="8b752-134">See also</span></span>

- [<span data-ttu-id="8b752-135">**Кнопки**</span><span class="sxs-lookup"><span data-stu-id="8b752-135">**Buttons**</span></span>](button.md)
- [<span data-ttu-id="8b752-136">**Интерактивный объект**</span><span class="sxs-lookup"><span data-stu-id="8b752-136">**Interactable**</span></span>](interactable.md)
