---
title: Общий доступ в Unity
description: Узнайте, как использовать одни и те же голограммы между несколькими пользователями в приложении Unity с пространственными привязками Azure.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Совместное использование, привязка, Ворлданчор, MR — совместное использование 250, Ворлданчортрансфербатч, Спатиалперцептион, Azure, пространственные привязки Azure, ASA, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: b9fdd09740dc6197c46a2d017f61e97898f213cd44bb504cbbf306f6a7ae21ec
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195926"
---
# <a name="shared-experiences-in-unity"></a>Общий доступ в Unity

совместное взаимодействие позволяет нескольким пользователям, каждому из которых назначено собственное устройство HoloLens, iOS или Android, совместно просматривать и взаимодействовать с одной голограммой. Голограммы располагаются в фиксированной точке в пространстве с помощью общего доступа к пространственной привязке.

## <a name="azure-spatial-anchors"></a>Пространственные привязки Azure

<a href="/azure/spatial-anchors/overview" target="_blank">пространственные привязки Azure</a> создают устойчивые облачные якорные привязки, которые приложение может разместить на нескольких устройствах HoloLens, iOS и Android.  При совместном использовании общей пространственной привязки на нескольких устройствах каждый пользователь может видеть содержимое, отображаемое относительно этой привязки в том же физическом расположении. 

можно также использовать <a href="/azure/spatial-anchors/overview" target="_blank">пространственные привязки Azure</a> для асинхронного сохранения голограмм на устройствах HoloLens, iOS и Android.  При совместном использовании пространственной геодоступной облачной привязки несколько устройств могут отслеживать одну и ту же голограмму с течением времени, даже если эти устройства не присутствуют одновременно.

Чтобы приступить к созданию общих интерфейсов в Unity, ознакомьтесь с пошаговыми руководствами Unity по 5-минутной <a href="/azure/spatial-anchors/unity-overview" target="_blank">пространственной привязке Azure</a>.

После настройки пространственных привязок Azure можно <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">создавать и искать привязки в Unity</a>.

## <a name="local-anchor-transfers"></a>Передача локальных привязок

в ситуациях, когда нельзя использовать пространственные привязки Azure, [передача локальных точек](../../out-of-scope/local-anchor-transfers-in-unity.md) подключения позволяет одному HoloLens устройству экспортировать привязку, чтобы вторая HoloLens могла импортировать его.  Этот подход не поддерживается на устройствах iOS и Android и обеспечивает менее устойчивое отзыв, чем пространственные привязки Azure.

## <a name="next-development-checkpoint"></a>Следующий этап разработки

Если вы подготовились к расположению разработки Unity, мы собрались изучить возможности и API платформы смешанной реальности. Отсюда можно перейти к следующему разделу:

> [!div class="nextstepaction"]
> [Камера с определяемым местоположением](locatable-camera-in-unity.md)

Или сразу перейдите к развертыванию приложения на устройстве или эмуляторе:

> [!div class="nextstepaction"]
> [развертывание в HoloLens или Windows Mixed Reality впечатляющих головных телефонов](../platform-capabilities-and-apis/using-visual-studio.md)

Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#3-advanced-features).

## <a name="see-also"></a>См. также раздел
* [Общий доступ в смешанной реальности](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Пространственные привязки Azure</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Пакет SDK для пространственных привязок Azure для Unity</a>