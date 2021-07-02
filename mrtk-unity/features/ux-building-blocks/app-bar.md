---
title: Панель приложения
description: Общие сведения о панели приложений в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, панель приложений,
ms.openlocfilehash: 3c8633d91b2c26f8bdc774a98b2cb48ffb276720
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175697"
---
# <a name="app-bar"></a><span data-ttu-id="7c2ce-104">Панель приложения</span><span class="sxs-lookup"><span data-stu-id="7c2ce-104">App bar</span></span>

![Панель приложения](../images/app-bar/MRTK_AppBar_Main.png)

<span data-ttu-id="7c2ce-106">Панель приложений — это компонент пользовательского интерфейса, который используется вместе с сценарием [элемента управления Bounds](bounds-control.md) .</span><span class="sxs-lookup"><span data-stu-id="7c2ce-106">App bar is a UI component that is used together with the [bounds control](bounds-control.md) script.</span></span> <span data-ttu-id="7c2ce-107">Он добавляет элементы управления "Кнопка" в объект с намерением управлять им.</span><span class="sxs-lookup"><span data-stu-id="7c2ce-107">It adds button controls to an object with the intent to manipulate it.</span></span> <span data-ttu-id="7c2ce-108">С помощью кнопки "настроить" можно отменить или активировать интерфейс управления границами для объекта.</span><span class="sxs-lookup"><span data-stu-id="7c2ce-108">Using the 'Adjust' button, the bounds control interface for an object can be de- / activated.</span></span> <span data-ttu-id="7c2ce-109">Кнопка "Удалить" должна удалить объект из сцены.</span><span class="sxs-lookup"><span data-stu-id="7c2ce-109">The "Remove" button should remove the object from the scene.</span></span>

## <a name="how-to-use-app-bar"></a><span data-ttu-id="7c2ce-110">Использование панели приложений</span><span class="sxs-lookup"><span data-stu-id="7c2ce-110">How to use app bar</span></span>

<span data-ttu-id="7c2ce-111">Перетащите `AppBar` (Assets/мртк/SDK/Features/UX/Prefabs/панель приложений/панель приложений. prefab) в иерархию сцены.</span><span class="sxs-lookup"><span data-stu-id="7c2ce-111">Drag and drop `AppBar` (Assets/MRTK/SDK/Features/UX/Prefabs/AppBar/AppBar.prefab) into the scene hierarchy.</span></span> <span data-ttu-id="7c2ce-112">На панели инспектора компонента назначьте любой объект с элементом управления Bounds в качестве *целевого ограничивающего прямоугольника* , чтобы добавить в него панель приложений.</span><span class="sxs-lookup"><span data-stu-id="7c2ce-112">In the inspector panel of the component, assign any object with a bounds control as the *Target Bounding Box* to add the app bar to it.</span></span>

<span data-ttu-id="7c2ce-113">**Важно.** Параметр активации элемента управления boundss для целевого объекта должен иметь значение "активировать вручную".</span><span class="sxs-lookup"><span data-stu-id="7c2ce-113">**Important:** The bounds control activation option for the target object should be 'Activate Manually'.</span></span>

<img src="../images/app-bar/MRTK_AppBar_Setup1.png" width="450" alt="Setup 1">

<img src="../images/app-bar/MRTK_AppBar_Setup2.png" width="450" alt="Set up 2">
