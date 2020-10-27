---
title: HP reverbы G2 контроллеров в нереальном режиме
description: Инструкции по использованию контроллеров HP reverbа G2 в Опенкср и Стеамвр
author: hferrone
ms.author: jacksonf
ms.date: 10/9/2020
ms.topic: article
keywords: Нереал, Нереал. 4, UE4, переглаголы, переглаголы G2, HP reverbы G2, Смешанная реальность, разработка, контроллеры движения, ввод данных пользователем, функции, новый проект, эмулятор, документация, руководства, функции, голограммы, Разработка игр
ms.openlocfilehash: c9d3ea3a8dd52ed0712f9df5c1a789121a68fd35
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638724"
---
# <a name="hp-reverb-g2-controllers-in-unreal"></a><span data-ttu-id="24c48-104">HP reverbы G2 контроллеров в нереальном режиме</span><span class="sxs-lookup"><span data-stu-id="24c48-104">HP Reverb G2 Controllers in Unreal</span></span> 

## <a name="getting-started"></a><span data-ttu-id="24c48-105">Начало работы</span><span class="sxs-lookup"><span data-stu-id="24c48-105">Getting started</span></span>

> [!IMPORTANT]
> <span data-ttu-id="24c48-106">Для доступа к подключаемому модулю контроллера движения HP требуется нереалия ядра 4,26 и Опенкср или Стеамвр. вам потребуется работать с контроллерами HP с переглаголом G2.</span><span class="sxs-lookup"><span data-stu-id="24c48-106">Unreal Engine 4.26 and either OpenXR or SteamVR is required to access the HP Motion Controller plugin you'll need to work with the HP Reverb G2 controllers.</span></span>

[!INCLUDE[](includes/tabs-g2-controllers-in-unreal.md)]

## <a name="porting-an-existing-openxr-app"></a><span data-ttu-id="24c48-107">Перенос существующего приложения Опенкср</span><span class="sxs-lookup"><span data-stu-id="24c48-107">Porting an existing OpenXR app</span></span> 

<span data-ttu-id="24c48-108">Если в игре для контроллера HP Mixed Reality не существует привязок контроллера, среда выполнения Опенкср попытается сопоставить существующие привязки с активным контроллером.</span><span class="sxs-lookup"><span data-stu-id="24c48-108">If no controller bindings exist in the game for the HP Mixed Reality Controller, the OpenXR runtime will attempt to remap the existing bindings to the active controller.</span></span>  <span data-ttu-id="24c48-109">В этом случае игра имеет Окулусные привязки касания и не содержит привязки контроллера HP Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="24c48-109">In this case, the game has Oculus Touch bindings and no HP Mixed Reality Controller bindings.</span></span>

![Повторное сопоставление существующих привязок при отсутствии привязок к контроллеру](images/reverb-g2-img-04.png)

<span data-ttu-id="24c48-111">События по-прежнему будут срабатывать, но если в игре необходимо использовать привязки для конкретных контроллеров, как в правой кнопке меню, необходимо использовать профиль взаимодействия HP Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="24c48-111">The events will still fire, but if the game needs to make use of controller specific bindings, like the right menu button, the HP Mixed Reality interaction profile must be used.</span></span>  <span data-ttu-id="24c48-112">Можно указать несколько привязок контроллера для каждого действия, чтобы обеспечить лучшую поддержку различных устройств.</span><span class="sxs-lookup"><span data-stu-id="24c48-112">Multiple controller bindings can be specified per action to better support different devices.</span></span>
   
![Использование нескольких привязок к контроллеру](images/reverb-g2-img-05.png)

## <a name="adding-input-action-mappings"></a><span data-ttu-id="24c48-114">Добавление сопоставлений входных действий</span><span class="sxs-lookup"><span data-stu-id="24c48-114">Adding input action mappings</span></span> 

<span data-ttu-id="24c48-115">Определите новое действие и сопоставьте его с одним из ключевых нажатий в разделе контроллера HP Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="24c48-115">Define a new action and map to one of the key presses in the HP Mixed Reality Controller section.</span></span>

![Определение новых действий и сопоставлений](images/reverb-g2-img-02.png)

<span data-ttu-id="24c48-117">Контроллер HP REVERB G2 также имеет аналоговый захват, который можно использовать в сопоставлениях осей с привязкой "сжатие по оси".</span><span class="sxs-lookup"><span data-stu-id="24c48-117">The HP Reverb G2 controller also has an analog grip, which can be used in the axis mappings with the “Squeeze Axis” binding.</span></span>  <span data-ttu-id="24c48-118">Существует отдельная привязка, которую следует использовать для сопоставлений действий при полной нажатии кнопки захвата.</span><span class="sxs-lookup"><span data-stu-id="24c48-118">There is a separate Squeeze binding, which should be used for action mappings when the grip button is fully pressed.</span></span> 

![Использование привязок осей сжатие](images/reverb-g2-img-03.png)

## <a name="adding-input-events"></a><span data-ttu-id="24c48-120">Добавление событий ввода</span><span class="sxs-lookup"><span data-stu-id="24c48-120">Adding input events</span></span>

<span data-ttu-id="24c48-121">Щелкните проект правой кнопкой мыши и выполните поиск новых имен действий из входной системы, чтобы добавить события для этих действий.</span><span class="sxs-lookup"><span data-stu-id="24c48-121">Right click on a Blueprint and search for the new action names from the input system to add events for these actions.</span></span>  <span data-ttu-id="24c48-122">Здесь проект отвечает на события со строкой печати, которая выводит текущую кнопку и состояние оси.</span><span class="sxs-lookup"><span data-stu-id="24c48-122">Here the Blueprint is responding to the events with a print string outputting the current button and axis state.</span></span>

![Схема реагирования на события и вывод текущей кнопки и состояния оси](images/reverb-g2-img-06.png)

### <a name="using-input"></a><span data-ttu-id="24c48-124">Использование входных данных</span><span class="sxs-lookup"><span data-stu-id="24c48-124">Using input</span></span> 

[!INCLUDE[](includes/tabs-g2-controller-mapping-in-unreal.md)]

## <a name="see-also"></a><span data-ttu-id="24c48-125">См. также статью</span><span class="sxs-lookup"><span data-stu-id="24c48-125">See also</span></span>
* [<span data-ttu-id="24c48-126">Входные данные Стеамвр</span><span class="sxs-lookup"><span data-stu-id="24c48-126">SteamVR Input</span></span>](https://docs.unrealengine.com/Platforms/VR/SteamVR/HowTo/SteamVRInput/index.html)
* [<span data-ttu-id="24c48-127">Использование Стеамвр с Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="24c48-127">Using SteamVR with Windows Mixed Reality</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)
* [<span data-ttu-id="24c48-128">Нереалная Камера проигрывателя</span><span class="sxs-lookup"><span data-stu-id="24c48-128">Unreal Player Camera</span></span>](https://docs.unrealengine.com/Programming/Tutorials/PlayerCamera/3/index.html)