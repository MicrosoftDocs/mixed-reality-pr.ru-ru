---
title: Общие пространственные привязки в DirectX
description: Узнайте, как синхронизировать два устройства HoloLens путем совместного использования локальных и пространственных привязок Azure в приложениях DirectX.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: HoloLens, синхронизация, пространственный якорь, перемещение, многопрограммный, просмотр, сценарий, пошаговое руководство, пример кода, Azure, пространственные привязки Azure, ASA
ms.openlocfilehash: 46fe6be5d81a8fc68502500e318eb8e63d223089
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008534"
---
# <a name="shared-experiences-in-directx"></a>Общие возможности DirectX

> [!NOTE]
> Эта статья связана с устаревшими собственными API-интерфейсами WinRT.  Для новых проектов собственных приложений рекомендуется использовать **[API опенкср](../native/openxr-getting-started.md)**.

Совместная работа — это один из нескольких пользователей с собственным устройством HoloLens, iOS или Android, совместное представление и взаимодействие с одной голограммой. Голограмма располагается в фиксированной точке с помощью общего доступа к пространственной привязке.

## <a name="azure-spatial-anchors"></a>Пространственные привязки Azure

<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Пространственные привязки Azure</a> можно использовать для создания устойчивых облачных пространственных привязок, которые приложение может разместить на нескольких устройствах HoloLens, iOS и Android.  При совместном использовании общей пространственной привязки на нескольких устройствах каждый пользователь может видеть содержимое, отображаемое относительно этой привязки в том же физическом расположении.  Это позволяет обмениваться опытом в режиме реального времени.

Можно также использовать <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Пространственные привязки Azure</a> для асинхронного сохранения голограмм на устройствах HoloLens, iOS и Android.  При совместном использовании пространственной геодоступной облачной привязки несколько устройств могут отслеживать одну и ту же голограмму с течением времени, даже если эти устройства не присутствуют одновременно.

Чтобы приступить к созданию общих интерфейсов в приложении HoloLens, ознакомьтесь с кратким руководством по HoloLens в течение 5 минут для <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">пространственных привязок Azure</a>.

После завершения работы с пространственными привязками Azure можно <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">создавать и размещать привязки на HoloLens</a>.  Также доступны пошаговые руководства для <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android и iOS</a> , что позволяет использовать одни и те же привязки на всех устройствах.

## <a name="local-anchor-transfers"></a>Передача локальных привязок

В ситуациях, когда нельзя использовать пространственные привязки Azure, [Передача локальных точек](../../out-of-scope/local-anchor-transfers-in-directx.md) подключения позволяет одному устройству hololens экспортировать привязку, которая будет импортирована вторым устройством hololens.  Такой подход обеспечивает менее устойчивое отзыв, чем пространственные привязки Azure, а устройства iOS и Android не поддерживаются этим подходом.

## <a name="see-also"></a>См. также раздел

* [Общий доступ в смешанной реальности](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Пространственные привязки Azure</a>
* <a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">Пакет SDK для пространственных привязок Azure для HoloLens</a>