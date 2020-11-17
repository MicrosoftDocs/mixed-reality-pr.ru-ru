---
title: Общий доступ в Unity
description: Совместное использование одних и тех же голограмм между несколькими пользователями в приложении Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Совместное использование, привязка, Ворлданчор, MR — совместное использование 250, Ворлданчортрансфербатч, Спатиалперцептион, Azure, пространственные привязки Azure, ASA, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: c9f432a2ef26e28a2329f9fd191f680a4148ca7e
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678463"
---
# <a name="shared-experiences-in-unity"></a>Общий доступ в Unity

Совместный опыт — это один из нескольких пользователей, каждый из которых имеет собственное устройство HoloLens, iOS или Android, совместное представление и взаимодействие с одной голограммой, которая находится в фиксированном месте. Это достигается благодаря совместному использованию пространственной привязки.

## <a name="azure-spatial-anchors"></a>Пространственные привязки Azure

<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Пространственные привязки Azure</a> можно использовать для создания устойчивых облачных пространственных привязок, которые приложение может разместить на нескольких устройствах HoloLens, iOS и Android.  При совместном использовании общей пространственной привязки на нескольких устройствах каждый пользователь может видеть содержимое, отображаемое относительно этой привязки в том же физическом расположении.  Это позволяет обмениваться опытом в режиме реального времени.

<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Пространственные привязки Azure</a> можно также использовать для сохранения асинхронной голограммы на устройствах HoloLens, iOS и Android.  Благодаря совместному использованию надежной облачной пространственной привязки несколько устройств могут наблюдать одну и ту же постоянную голограмму с течением времени, даже если они находятся в разное время в разных местах.

Чтобы приступить к созданию общих интерфейсов в Unity, ознакомьтесь с пошаговыми руководствами Unity по 5-минутной <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">пространственной привязке Azure</a>.

После завершения работы с пространственными привязками Azure можно <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">создавать и искать привязки в Unity</a>.

## <a name="local-anchor-transfers"></a>Передача локальных привязок

В ситуациях, когда нельзя использовать пространственные привязки Azure, [Передача локальных точек](../../out-of-scope/local-anchor-transfers-in-unity.md) подключения позволяет одному устройству hololens экспортировать привязку, которая будет импортирована вторым устройством hololens.  Обратите внимание, что этот подход обеспечивает менее устойчивое отзыв, чем пространственные привязки Azure, а устройства iOS и Android не поддерживаются этим подходом.

## <a name="next-development-checkpoint"></a>Следующий этап разработки

Если вы используете точку контрольной точки разработки Unity, которую мы собрали, вы находитесь в процессе изучения возможностей платформы смешанной реальности и интерфейсов API. Отсюда вы можете перейти к следующей теме:

> [!div class="nextstepaction"]
> [Камера с определяемым местоположением](locatable-camera-in-unity.md)

Или сразу перейдите к развертыванию приложения на устройстве или эмуляторе:

> [!div class="nextstepaction"]
> [Развертывание в HoloLens или в виде впечатляющих головных телефонов Windows Mixed Reality](../platform-capabilities-and-apis/using-visual-studio.md)

Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#3-platform-capabilities-and-apis).

## <a name="see-also"></a>См. также раздел
* [Общий доступ в смешанной реальности](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Пространственные привязки Azure</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Пакет SDK для пространственных привязок Azure для Unity</a>
