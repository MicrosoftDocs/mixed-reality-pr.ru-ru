---
ms.openlocfilehash: bcd9ae057f289d85d1f12d5cb79258bc3bb87ace
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443701"
---
# <a name="425"></a>[<span data-ttu-id="76cc0-101">4.25</span><span class="sxs-lookup"><span data-stu-id="76cc0-101">4.25</span></span>](#tab/425)

<span data-ttu-id="76cc0-102">Дополнительные действия по включению для UE 4.25 не требуются.</span><span class="sxs-lookup"><span data-stu-id="76cc0-102">There are no additional enabling steps specific to UE 4.25.</span></span>

# <a name="426"></a>[<span data-ttu-id="76cc0-103">4.26</span><span class="sxs-lookup"><span data-stu-id="76cc0-103">4.26</span></span>](#tab/426)

<span data-ttu-id="76cc0-104">Если вы используете UE 4.26, мы рекомендуем использовать следующую настройку схемы для добавления небольшой задержки, так как отслеживание QR-кода должно быть инициализировано ПОСЛЕ запуска сеанса дополненной реальности:</span><span class="sxs-lookup"><span data-stu-id="76cc0-104">If you're using UE 4.26, we recommend using the following blueprint setup to add a small delay, because QR code tracking must be initialized AFTER starting an AR Session:</span></span>

![Схема функции Toggle ARCapture с задержкой](../images/qr-codes-img-01.png)
