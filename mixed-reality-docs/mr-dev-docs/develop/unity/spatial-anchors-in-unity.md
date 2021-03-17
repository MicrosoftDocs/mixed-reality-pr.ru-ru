---
title: Пространственные привязки в Unity
description: Узнайте, как создавать, хранить и извлекать пространственные привязки в приложениях Unity Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 03/16/2021
ms.topic: article
keywords: Unity, пространственные привязки, хранилище привязок, HoloLens, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 665cdae56f271a061972922af835ff64bdc35496
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/17/2021
ms.locfileid: "103623624"
---
# <a name="spatial-anchors-in-unity"></a>Пространственные привязки в Unity

Пространственные привязки сохраняют голограммы в реальных пространствах между сеансами приложения. После сохранения в хранилище привязки HoloLens они могут быть найдены и загружены в разные сеансы и являются идеальным вариантом отката при отсутствии подключения к Интернету.

> [!IMPORTANT]
> Локальные привязки хранятся на устройстве, а пространственные привязки Azure сохраняются в облаке. Если вы хотите использовать облачные службы Azure для хранения привязок, мы предоставляем документ, который поможем вам в интеграции [Пространственных привязок Azure](../mixed-reality-cloud-services.md#azure-spatial-anchors). Обратите внимание, что вы можете использовать локальные привязки и привязки Azure в одном проекте без каких-либо конфликтов.

## <a name="understanding-anchors"></a>Основные сведения о привязках

[!INCLUDE[](includes/unity-understanding-anchors.md)]

## <a name="using-the-anchorstore"></a>Использование Анчорсторе

[!INCLUDE[](includes/unity-spatial-anchorstore.md)]

## <a name="next-development-checkpoint"></a>Следующий этап разработки

Если вы используете точку контрольной точки разработки Unity, которую мы собрали, то можете изучить стандартные блоки в смешанной реальности. Отсюда вы можете перейти к следующему стандартному блоку:

> [!div class="nextstepaction"]
> [Пространственное сопоставление](spatial-mapping-in-unity.md)

Или перейдите к возможностям и API платформы смешанной реальности:

> [!div class="nextstepaction"]
> [общие возможности](shared-experiences-in-unity.md);

Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#2-core-building-blocks).

## <a name="see-also"></a>См. также
* [Сохраняемость пространственной привязки](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="/azure/spatial-anchors" target="_blank">Пространственные привязки Azure.</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Пакет SDK для пространственных привязок Azure для Unity</a>
* [Масштабирование работы](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [Пространственный этап](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Потеря слежения в Unity](tracking-loss-in-unity.md)
* [Пространственные привязки](../../design/spatial-anchors.md)
* [Общий доступ в Unity](shared-experiences-in-unity.md)