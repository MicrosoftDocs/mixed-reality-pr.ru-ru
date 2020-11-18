---
title: Покупки из приложений
description: Покупки из приложений поддерживаются в приложениях смешанной реальности, но для их настройки требуется определенная работа.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: покупки в приложении, hololens, XAML, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 07601ab4961e14ff43dbc149f7d8cb5731d24013
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703180"
---
# <a name="in-app-purchases"></a><span data-ttu-id="da8d0-104">Покупки из приложений</span><span class="sxs-lookup"><span data-stu-id="da8d0-104">In-app purchases</span></span>

<span data-ttu-id="da8d0-105">Покупки из приложений поддерживаются в HoloLens, но для их настройки требуется определенная работа.</span><span class="sxs-lookup"><span data-stu-id="da8d0-105">In-app purchases are supported in HoloLens, but there is some work to set them up.</span></span>

<span data-ttu-id="da8d0-106">Чтобы использовать функцию в функции приобретения приложений, необходимо:</span><span class="sxs-lookup"><span data-stu-id="da8d0-106">In order to leverage the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="da8d0-107">Создание 2D- [представления](../design/app-views.md) XAML для отображения в виде планшета</span><span class="sxs-lookup"><span data-stu-id="da8d0-107">Create a XAML [2D view](../design/app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="da8d0-108">Переключитесь на него, чтобы активировать размещение, которое оставляет иммерсивное представление</span><span class="sxs-lookup"><span data-stu-id="da8d0-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="da8d0-109">Вызовите API: await [куррентапп. рекуестпродуктпурчасеасинк ("дураблеитемиапнаме");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="da8d0-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="da8d0-110">Этот API отобразит всплывающее окно ОС Windows, в котором отображается название, описание и цена покупки в приложении.</span><span class="sxs-lookup"><span data-stu-id="da8d0-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="da8d0-111">Затем пользователь может выбрать вариант приобретения.</span><span class="sxs-lookup"><span data-stu-id="da8d0-111">The user can then choose purchase options.</span></span> <span data-ttu-id="da8d0-112">После завершения действия приложение должно предоставить пользовательский интерфейс, который позволяет пользователю вернуться в его [иммерсивное представление](../design/app-views.md).</span><span class="sxs-lookup"><span data-stu-id="da8d0-112">Once the action is completed, the app will need to present UI which allows the user to switch back to its [immersive view](../design/app-views.md).</span></span>

<span data-ttu-id="da8d0-113">Для приложений, предназначенных для впечатляющих головных телефонов Windows Mixed Reality, не требуется вручную переключаться на представление XAML перед вызовом API Рекуестпродуктпурчасеасинк.</span><span class="sxs-lookup"><span data-stu-id="da8d0-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it is not required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
