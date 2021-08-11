---
title: Остановка взгляда
description: Взаимодействие вдаваясь
author: cre8ivepark
ms.author: dongpark
ms.date: 05/20/2021
keywords: вдаваясь, Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 8ac63ee723cdd524ee7abbad7fd2658b446156adbd5ddee06ae1795edb3b68d1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226913"
---
# <a name="dwell"></a>Остановка взгляда

![Карточка остановки взгляда](../images/dwell/MRTK_UX_Dwell.png)

Head-взгляд и вдаваясь являются великолепной в ситуациях, когда руки человека заняты другими задачами. Эта функция также полезна, если речь не 100% надежности или доступности в связи с ограничениями на окружающую среду или социальные сети.
В примерах вдаваясь МРТК демонстрируются различные типы компонентов пользовательского интерфейса с настраиваемым временем отклика и визуальным отзывом.

Рекомендации по проектированию см. на странице с [рекомендациями Head и вдаваясь](/windows/mixed-reality/design/gaze-and-dwell-head) .

## <a name="dwell-scripts"></a>Вдаваясь сценарии

- **Двеллхандлер**: добавляет модальность вдаваясь к целевому объекту пользовательского интерфейса.
- **Двеллстатетипе**: состояния обработчика вдаваясь.
- **Двеллунитевент**: событие Unity для события вдаваясь. Содержит ссылку на указатель.
- **Баседвеллпрессаблебуттон. CS** : скрипт, который запускает событие OnClick () в `Interactable` PressableButtonHoloLens2 Prefabs.
- **Тоггледвеллпрессаблебуттон. CS** : этот скрипт изменяет `_BorderWidth` свойство объекта, `dwellVisualImage` который использует шейдер мртк Standard.

## <a name="dwell-profiles"></a>Профили вдаваясь
Профили вдаваясь используются **обработчиком вдаваясь** для настройки различных порогов.
- **Буттондвеллпрофиле. актив**
- **Инстанддвеллпрофиле. актив**
- **Двеллпрофилевисдекай. актив**

## <a name="prefabs"></a>Prefabs

эти prefabs являются вариантами HoloLens 2 стиля с нажатой кнопкой prefabs, которые имеют дополнительные компоненты для поддержки взаимодействий вдаваясь.

- **PressableButtonHoloLens2_Dwell. prefab**
- **PressableButtonHoloLens2_32x96_Dwell. prefab**
- **PressableButtonHoloLens2ToggleDwell. prefab**
- **PressableButtonHoloLens2Toggle_32x96_Dwell. prefab**

Эти Prefabs имеют дополнительный компонент **куаддвеллвисуал** для визуализации состояния ввода вдаваясь. У него есть **холографикбаккплатедвеллвисуал** материалов. **Тоггледвеллпрессаблебуттон. CS** обновляет свойство **_BorderWidth** стандартного шейдера мртк для визуализации входных данных вдаваясь.

<img src="../images/dwell/MRTK_UX_Dwell_Prefabs_Structure.png" alt="Dwell prefabs structure" width="550px">
<img src="../images/dwell/MRTK_UX_Dwell_Prefabs.png" alt="Dwell prefabs" width="350px">

## <a name="example-scene"></a>Пример сцены

Примеры можно найти в `DwellExample` сцене. В примере сцены показаны примеры пользовательского интерфейса объемные и примеры пользовательского интерфейса Unity.

<img src="../images/dwell/MRTK_UX_Dwell_Examples.png" alt="Near Menu Example">

## <a name="see-also"></a>См. также раздел

- [**Кнопки**](button.md)
- [**Интерактивный объект**](interactable.md)
