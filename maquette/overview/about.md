---
title: О Макуетте
description: Общие сведения о Макуетте и его возможностях.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Макуетте, создание прототипов, Смешанная реальность, виртуальная реальность, VR, MR, обратная связь, центр обратной связи, ошибки
ms.openlocfilehash: fbc2aee7472a26e508937fa1dedfdac08fadfa10
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935621"
---
# <a name="about-maquette"></a><span data-ttu-id="4652e-104">О Макуетте</span><span class="sxs-lookup"><span data-stu-id="4652e-104">About Maquette</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->
<span data-ttu-id="4652e-105">![](../images/MaquetteIcon.png)Общие сведения о макуеттескрипт логотипа</span><span class="sxs-lookup"><span data-stu-id="4652e-105">![Logo](../images/MaquetteIcon.png) MaquetteScript Introduction</span></span>

<!-- TODO(Harrison/Stefan): Add more high level, less technical explanation of what Maquette is and why it's useful in MR development. 
          - Differentiate between Maquette and MaquetteScript
          - Separate out each of Maquette's main parts and add content
          - Give brief explanations of use case or examples
-->
<span data-ttu-id="4652e-106">Макуетте интегрирует Стандартный ECMA 5,1 JavaScript, чтобы обеспечить инвестиции в Макуетте сцены и объекты, которые можно редактировать и выполнять в VSCode.</span><span class="sxs-lookup"><span data-stu-id="4652e-106">Maquette integrates standard ECMA 5.1 Javascript to enable investment of interactivity in Maquette scenes and objects which can be edited and executed from within VSCode.</span></span> <span data-ttu-id="4652e-107">Свойства объектов предоставляются для чтения и настройки из скрипта, вызванных методов объектов, а объектов и системных событий.</span><span class="sxs-lookup"><span data-stu-id="4652e-107">Properties of objects are exposed for reading and setting from within script, object methods called, and object and system events fielded.</span></span> <span data-ttu-id="4652e-108">Скрипт также может взаимодействовать с Макуетте с помощью системных объектов, доступных через скрипт.</span><span class="sxs-lookup"><span data-stu-id="4652e-108">Script can also interact with Maquette itself via system objects accessible via script.</span></span> <span data-ttu-id="4652e-109">Различные элементы управления пользовательского интерфейса, с которыми может взаимодействовать пользователь, являются частью системы.</span><span class="sxs-lookup"><span data-stu-id="4652e-109">Various UI controls that the user can interact with are part of the system.</span></span> <span data-ttu-id="4652e-110">Они могут быть добавлены при создании в Макуетте, а также в процессе создания и управления из скрипта.</span><span class="sxs-lookup"><span data-stu-id="4652e-110">These can be added when authoring in Maquette or created and managed from within script.</span></span> <span data-ttu-id="4652e-111">События взаимодействия с пользователем с этими элементами (ввод данных, щелчки и т. д.) также предоставляются в скрипты как события.</span><span class="sxs-lookup"><span data-stu-id="4652e-111">User interaction events with these elements (data entry, clicks, etc) are also exposed to script as events.</span></span> <span data-ttu-id="4652e-112">Благодаря этим дополнениям можно создавать простые и сложные сцены, от экспериментов до визуализации данных и изучения пользовательских сценариев смешанной реальности до полностью реализованных возможностей AR или VR.</span><span class="sxs-lookup"><span data-stu-id="4652e-112">With these additions, simple to complex scenes can be built, from experiments to data visualization to explorations of Mixed Reality user scenarios to fully realized experiences in AR or VR.</span></span>

<p align="center">
  <img src="images/ScriptingOverview.png" alt="Scripting overview video screenshot">
</p>

<!-- TODO(Harrison/Stefan): Get this video recorded or create the content in text form until it's available. -->
<span data-ttu-id="4652e-113">60 секонд'иш видео</span><span class="sxs-lookup"><span data-stu-id="4652e-113">60 second'ish video</span></span>
* <span data-ttu-id="4652e-114">Карточка заголовка записи</span><span class="sxs-lookup"><span data-stu-id="4652e-114">Entry Title Card</span></span>
  * <span data-ttu-id="4652e-115">Создание интерактивного содержимого смешанной реальности в Макуетте</span><span class="sxs-lookup"><span data-stu-id="4652e-115">Creation of Interactive Mixed Reality Content in Maquette</span></span>
  * <span data-ttu-id="4652e-116">Работа с скриптами, интерактивными системами и интерфейсами пользователя</span><span class="sxs-lookup"><span data-stu-id="4652e-116">Scripting/Interactivity/UI System</span></span>
* <span data-ttu-id="4652e-117">ВО в приветствии для субтитров группы или видео?</span><span class="sxs-lookup"><span data-stu-id="4652e-117">VO welcome by team or video captions?</span></span>  <span data-ttu-id="4652e-118">объясня</span><span class="sxs-lookup"><span data-stu-id="4652e-118">explaining:</span></span>
  * <span data-ttu-id="4652e-119">Включение сценариев для создания интерактивного содержимого MR</span><span class="sxs-lookup"><span data-stu-id="4652e-119">reasoning behind scripting to enable creation of interactive MR content</span></span>
  * <span data-ttu-id="4652e-120">касание того, как его можно использовать в очень широких штрихах кистей</span><span class="sxs-lookup"><span data-stu-id="4652e-120">touch on how it can be used in very broad brush strokes</span></span>
* <span data-ttu-id="4652e-121">Создание скриптов в действии винжетте</span><span class="sxs-lookup"><span data-stu-id="4652e-121">Scripting vingette’s in action</span></span>
  * <span data-ttu-id="4652e-122">Диалоговое окно «составление»</span><span class="sxs-lookup"><span data-stu-id="4652e-122">Composing dialog box</span></span>
  * <span data-ttu-id="4652e-123">Создание приложения на основе структуры (демонстрация приложения кулинарной программы)</span><span class="sxs-lookup"><span data-stu-id="4652e-123">Building app from outline (cooking app demo)</span></span>
  * <span data-ttu-id="4652e-124">Составление в модели фотограмметри</span><span class="sxs-lookup"><span data-stu-id="4652e-124">Composing in photogrammetry model</span></span>
  * <span data-ttu-id="4652e-125">Руководство по устранению неполадок</span><span class="sxs-lookup"><span data-stu-id="4652e-125">Interacting with troubleshooting guide</span></span>
  * <span data-ttu-id="4652e-126">Экранное представление отладки сценариев в VSCode</span><span class="sxs-lookup"><span data-stu-id="4652e-126">Screen view of debugging scripting in VSCode</span></span>
  * <span data-ttu-id="4652e-127">Получение доступа к сценарию из объекта в сцене</span><span class="sxs-lookup"><span data-stu-id="4652e-127">Getting access to script from an object in scene</span></span>
  * <span data-ttu-id="4652e-128">И т. д.</span><span class="sxs-lookup"><span data-stu-id="4652e-128">Etc...</span></span>
* <span data-ttu-id="4652e-129">Сводный заголовок карточка в конце</span><span class="sxs-lookup"><span data-stu-id="4652e-129">Summary Title card at end</span></span>
  * <span data-ttu-id="4652e-130">Ссылка на Макуетте</span><span class="sxs-lookup"><span data-stu-id="4652e-130">Link to Maquette</span></span>
  * <span data-ttu-id="4652e-131">Где перейти, чтобы приступить к работе со сценариями</span><span class="sxs-lookup"><span data-stu-id="4652e-131">Where to go to get started with scripting</span></span>
  * <span data-ttu-id="4652e-132">Объявления, состояние и сообщество</span><span class="sxs-lookup"><span data-stu-id="4652e-132">Announcements/status/community</span></span>
  * <span data-ttu-id="4652e-133">Взгляните вперед, чтобы узнать, что вы можете сделать (?)</span><span class="sxs-lookup"><span data-stu-id="4652e-133">Look forward to seeing what you can do/submissions(?)</span></span>
  * <span data-ttu-id="4652e-134">Обратная связь и как мы сможем помочь вам лучше</span><span class="sxs-lookup"><span data-stu-id="4652e-134">Feedback and how we can serve you better</span></span>

<!-- TODO(Harrison): Consider breaking this out into a Maquette journey doc or section as applicable. -->
* [<span data-ttu-id="4652e-135">Начало работы</span><span class="sxs-lookup"><span data-stu-id="4652e-135">Getting Started</span></span>](installation.md)
* [<span data-ttu-id="4652e-136">Примеры и образцы приложений</span><span class="sxs-lookup"><span data-stu-id="4652e-136">Examples and Sample Apps</span></span>](../samples/overview.md)
* [<span data-ttu-id="4652e-137">Поддержка</span><span class="sxs-lookup"><span data-stu-id="4652e-137">Support</span></span>](../resources/support.md)

<!-- TODO(Harrison): Need to find out why docs feedback footer isn't appearing. -->
## <a name="send-us-feedback"></a><span data-ttu-id="4652e-138">Отправка отзыва</span><span class="sxs-lookup"><span data-stu-id="4652e-138">Send us feedback</span></span>

<span data-ttu-id="4652e-139">Мы будем рады узнать о своих впечатлениях и результатах.</span><span class="sxs-lookup"><span data-stu-id="4652e-139">We look forward to hearing about your experiences and results.</span></span> <span data-ttu-id="4652e-140">Отзывы, предложения и отчеты об ошибках всегда Добро пожаловать!</span><span class="sxs-lookup"><span data-stu-id="4652e-140">Feedback, suggestions and bug reports always welcome!</span></span>
<span data-ttu-id="4652e-141"><ссылку? ></span><span class="sxs-lookup"><span data-stu-id="4652e-141"><Link?></span></span>