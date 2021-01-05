---
title: Покупки из приложений
description: Покупки из приложений поддерживаются в приложениях смешанной реальности, но для их настройки требуется некоторое количество операций.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: покупки в приложении, hololens, XAML, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 905c1be72bf2a3d6fa167cab68a4cb71e6538acc
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757787"
---
# <a name="in-app-purchases"></a><span data-ttu-id="e00d8-104">Покупки из приложений</span><span class="sxs-lookup"><span data-stu-id="e00d8-104">In-app purchases</span></span>

<span data-ttu-id="e00d8-105">Покупки из приложений поддерживаются в HoloLens, но для их настройки требуется некоторое количество операций.</span><span class="sxs-lookup"><span data-stu-id="e00d8-105">In-app purchases are supported in HoloLens, but there's some work to set them up.</span></span>

<span data-ttu-id="e00d8-106">Чтобы использовать функцию в функции приобретения приложений, необходимо выполнить следующие действия.</span><span class="sxs-lookup"><span data-stu-id="e00d8-106">To use the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="e00d8-107">Создание 2D- [представления](../design/app-views.md) XAML для отображения в виде планшета</span><span class="sxs-lookup"><span data-stu-id="e00d8-107">Create a XAML [2D view](../design/app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="e00d8-108">Переключитесь на него, чтобы активировать размещение, которое оставляет иммерсивное представление</span><span class="sxs-lookup"><span data-stu-id="e00d8-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="e00d8-109">Вызовите API: await [куррентапп. рекуестпродуктпурчасеасинк ("дураблеитемиапнаме");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="e00d8-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="e00d8-110">Этот API отобразит всплывающее окно ОС Windows, в котором отображается название, описание и цена покупки в приложении.</span><span class="sxs-lookup"><span data-stu-id="e00d8-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="e00d8-111">Затем пользователь может выбрать вариант приобретения.</span><span class="sxs-lookup"><span data-stu-id="e00d8-111">The user can then choose purchase options.</span></span> <span data-ttu-id="e00d8-112">После завершения действия приложение должно будет представлять пользовательский интерфейс, что позволит пользователю вернуться к его [иммерсивное представление](../design/app-views.md).</span><span class="sxs-lookup"><span data-stu-id="e00d8-112">Once the action is completed, the app will need to present UI, which allows the user to switch back to its [immersive view](../design/app-views.md).</span></span>

<span data-ttu-id="e00d8-113">Для приложений, предназначенных для настольных и впечатляющих головных телефонов Windows Mixed Reality, не требуется вручную переключаться на представление XAML перед вызовом API Рекуестпродуктпурчасеасинк.</span><span class="sxs-lookup"><span data-stu-id="e00d8-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it isn't required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
