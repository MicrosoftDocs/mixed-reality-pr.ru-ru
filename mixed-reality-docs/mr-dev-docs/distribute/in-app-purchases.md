---
title: Покупки из приложений
description: Узнайте, как использовать покупки из приложений в приложениях смешанной реальности с помощью 2D-представлений XAML и всплывающего окна ОС Windows для хранения.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: покупки в приложении, hololens, XAML, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: dfc5a0cfcc7a4d63147a753c8892d65dfae5e495
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582950"
---
# <a name="in-app-purchases"></a><span data-ttu-id="4816a-104">Покупки из приложений</span><span class="sxs-lookup"><span data-stu-id="4816a-104">In-app purchases</span></span>

<span data-ttu-id="4816a-105">Покупки из приложений поддерживаются в HoloLens, но для их настройки требуется некоторое количество операций.</span><span class="sxs-lookup"><span data-stu-id="4816a-105">In-app purchases are supported in HoloLens, but there's some work to set them up.</span></span>

<span data-ttu-id="4816a-106">Чтобы использовать функцию в функции приобретения приложений, необходимо выполнить следующие действия.</span><span class="sxs-lookup"><span data-stu-id="4816a-106">To use the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="4816a-107">Создание 2D- [представления](../design/app-views.md) XAML для отображения в виде планшета</span><span class="sxs-lookup"><span data-stu-id="4816a-107">Create a XAML [2D view](../design/app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="4816a-108">Переключитесь на него, чтобы активировать размещение, которое оставляет иммерсивное представление</span><span class="sxs-lookup"><span data-stu-id="4816a-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="4816a-109">Вызовите API: await [куррентапп. рекуестпродуктпурчасеасинк ("дураблеитемиапнаме");](/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="4816a-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="4816a-110">Этот API отобразит всплывающее окно ОС Windows, в котором отображается название, описание и цена покупки в приложении.</span><span class="sxs-lookup"><span data-stu-id="4816a-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="4816a-111">Затем пользователь может выбрать вариант приобретения.</span><span class="sxs-lookup"><span data-stu-id="4816a-111">The user can then choose purchase options.</span></span> <span data-ttu-id="4816a-112">После завершения действия приложение должно будет представлять пользовательский интерфейс, что позволит пользователю вернуться к его [иммерсивное представление](../design/app-views.md).</span><span class="sxs-lookup"><span data-stu-id="4816a-112">Once the action is completed, the app will need to present UI, which allows the user to switch back to its [immersive view](../design/app-views.md).</span></span>

<span data-ttu-id="4816a-113">Для приложений, предназначенных для настольных и впечатляющих головных телефонов Windows Mixed Reality, не требуется вручную переключаться на представление XAML перед вызовом API Рекуестпродуктпурчасеасинк.</span><span class="sxs-lookup"><span data-stu-id="4816a-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it isn't required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>