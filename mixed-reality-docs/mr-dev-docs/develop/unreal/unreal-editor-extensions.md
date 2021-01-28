---
title: Расширения редактора в Unreal
description: Сведения о том, как дополнить редактор Unreal Engine пользовательскими скриптами, заданными действиями и мини-приложениями служебных программ.
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, расширения редактора, редактор Unreal, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, документация, руководства, функции, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, перенос, обновление
ms.openlocfilehash: ee0ba5d1d60b83dc334204e12283c76a877b4ec8
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/20/2021
ms.locfileid: "98584919"
---
# <a name="editor-extensions-in-unreal"></a><span data-ttu-id="ca2a6-104">Расширения редактора в Unreal</span><span class="sxs-lookup"><span data-stu-id="ca2a6-104">Editor extensions in Unreal</span></span>

<span data-ttu-id="ca2a6-105">Unreal предоставляет широкий набор возможностей, с помощью которых вы можете настроить систему под ваши требования.</span><span class="sxs-lookup"><span data-stu-id="ca2a6-105">Unreal provides an extensive set of features that allow you to customize the engine to your needs.</span></span> <span data-ttu-id="ca2a6-106">Это могут быть как простые и ограниченные возможности, так и очень мощные и сложные.</span><span class="sxs-lookup"><span data-stu-id="ca2a6-106">The features range from simple but limited, to very powerful but complex.</span></span> <span data-ttu-id="ca2a6-107">Ниже перечислены шаги в порядке возрастания сложности.</span><span class="sxs-lookup"><span data-stu-id="ca2a6-107">The following steps are listed in order of increasing complexity.</span></span> <span data-ttu-id="ca2a6-108">Как правило, для решения проблемы сначала нужно попробовать простые решения, а только затем переходить к более сложным.</span><span class="sxs-lookup"><span data-stu-id="ca2a6-108">In general, you should reach for simpler solutions to your problem, and exhausting its options, before moving to a more complex option.</span></span> <span data-ttu-id="ca2a6-109">Например, простейший скрипт конструирования в большинстве случаев успешно применим вместо подключаемых модулей.</span><span class="sxs-lookup"><span data-stu-id="ca2a6-109">As an example, we have found that the basic Construction Script can be used in lieu of plugins most of the time.</span></span> 

<!-- Also, engine modification should be a last resort, as it is not only complex, but integrating changes back into the engine for simple work-around can take a disproportionately long time. -->

## <a name="construction-scripts"></a><span data-ttu-id="ca2a6-110">Скрипты конструирования</span><span class="sxs-lookup"><span data-stu-id="ca2a6-110">Construction scripts</span></span>

<span data-ttu-id="ca2a6-111">Скрипты конструирования можно использовать для выполнения действий инициализации, которые выполняются при создании экземпляра схемы.</span><span class="sxs-lookup"><span data-stu-id="ca2a6-111">You can use construction scripts to perform initialization actions, which run when Blueprint instance are created.</span></span>

* [<span data-ttu-id="ca2a6-112">Пользовательский скрипт конструирования</span><span class="sxs-lookup"><span data-stu-id="ca2a6-112">User Constructions script</span></span>](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)
* [<span data-ttu-id="ca2a6-113">Пример схемы</span><span class="sxs-lookup"><span data-stu-id="ca2a6-113">Blueprint example</span></span>](https://docs.unrealengine.com/Resources/ContentExamples/Blueprints/1_4/index.html)
* [<span data-ttu-id="ca2a6-114">Видеоруководство</span><span class="sxs-lookup"><span data-stu-id="ca2a6-114">Video tutorial</span></span>](https://www.youtube.com/watch?v=z1SD-d9yJmQ&ab_channel=UnrealEngine)

## <a name="scripted-actions"></a><span data-ttu-id="ca2a6-115">Заданные действия</span><span class="sxs-lookup"><span data-stu-id="ca2a6-115">Scripted actions</span></span>

<span data-ttu-id="ca2a6-116">Заданные действия — это схемы служебных программ для редактора.</span><span class="sxs-lookup"><span data-stu-id="ca2a6-116">Scripted Actions are Editor Utility Blueprints.</span></span> <span data-ttu-id="ca2a6-117">Их можно запустить в редакторе Unreal, выполнив следующие действия:</span><span class="sxs-lookup"><span data-stu-id="ca2a6-117">You can launch them in the Unreal Editor by:</span></span>
* <span data-ttu-id="ca2a6-118">Щелкните правой кнопкой мыши элемент **Assets** (Активы) в обозревателе содержимого.</span><span class="sxs-lookup"><span data-stu-id="ca2a6-118">Right-clicking **Assets** in the Content Browser</span></span>
* <span data-ttu-id="ca2a6-119">Или щелкните правой кнопкой мыши элемент **Actors** (Субъекты) в окнах просмотра уровня или структуры мира.</span><span class="sxs-lookup"><span data-stu-id="ca2a6-119">Or by right-clicking **Actors** either in the Level Viewport or in the World Outliner</span></span>

<span data-ttu-id="ca2a6-120">Заданные действия идеально подходят для тех случаев, когда логика схемы должна иметь контекстуальные сведения о наборах активов или субъектов.</span><span class="sxs-lookup"><span data-stu-id="ca2a6-120">Scripted Actions are uniquely suited for times when you need your Blueprint logic to have contextual awareness about sets of Assets or Actors.</span></span> <span data-ttu-id="ca2a6-121">Обычно заданное действие получает список активов или субъектов, которые вы выбрали при запуске этого действия, а затем изменяет эти объекты или включает их в свой граф.</span><span class="sxs-lookup"><span data-stu-id="ca2a6-121">Typically, a Scripted Action gets a list of Assets or Actors that you've selected when the action is executed, then modifies those objects or considers them in its graph.</span></span>

* [<span data-ttu-id="ca2a6-122">Заданные действия</span><span class="sxs-lookup"><span data-stu-id="ca2a6-122">Scripted Actions</span></span>](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/ScriptedActions/index.html)
* [<span data-ttu-id="ca2a6-123">Запуск заданных действий при запуске проекта</span><span class="sxs-lookup"><span data-stu-id="ca2a6-123">Running scripted actions on project startup</span></span>](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/StartupObjects/index.html)

## <a name="editor-utility-widgets"></a><span data-ttu-id="ca2a6-124">Мини-приложения служебной программы редактора</span><span class="sxs-lookup"><span data-stu-id="ca2a6-124">Editor utility widgets</span></span>

<span data-ttu-id="ca2a6-125">[Мини-приложения служебной программы редактора](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) удобно использовать, когда нужно добавить новые элементы в пользовательский интерфейс редактора Unreal.</span><span class="sxs-lookup"><span data-stu-id="ca2a6-125">You can use [Editor Utility Widgets](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) anytime you want to add new UI elements to modify the User Interface (UI) of the Unreal Editor.</span></span> <span data-ttu-id="ca2a6-126">Мини-приложения служебной программы редактора основаны на подсистеме UMG (Unreal Motion Graphics), поэтому вы можете настраивать мини-приложения в схеме так же, как и для любой другой схемы мини-приложения UMG.</span><span class="sxs-lookup"><span data-stu-id="ca2a6-126">Editor Utility Widgets are based on Unreal Motion Graphics (UMG), so you can set up Widgets in a Blueprint like you would for any other UMG Widget Blueprint.</span></span>

<span data-ttu-id="ca2a6-127">Эти мини-приложения предназначены специально для пользовательского интерфейса редактора, и с их помощью можно создать настраиваемые вкладки редактора.</span><span class="sxs-lookup"><span data-stu-id="ca2a6-127">These Widgets are specifically for the Editor UI, and you can use them to create custom Editor tabs.</span></span> <span data-ttu-id="ca2a6-128">Затем можно выбрать эти настраиваемые вкладки в меню Windows (как обычные вкладки редактора).</span><span class="sxs-lookup"><span data-stu-id="ca2a6-128">You can then select these custom tabs from the Windows menu, like you would select existing Editor tabs.</span></span>

## <a name="plugins"></a><span data-ttu-id="ca2a6-129">Подключаемые модули</span><span class="sxs-lookup"><span data-stu-id="ca2a6-129">Plugins</span></span>

<span data-ttu-id="ca2a6-130">Unreal позволяет разрабатывать собственные пользовательские [подключаемые модули](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html) и управлять ими для применения в средствах и среде выполнения UE4.</span><span class="sxs-lookup"><span data-stu-id="ca2a6-130">Unreal lets you develop and manage your own custom [plugins](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html) for use with UE4 tools and runtime.</span></span> <span data-ttu-id="ca2a6-131">Вы можете в любое время включить или отключить подключаемые модули в редакторе Unreal.</span><span class="sxs-lookup"><span data-stu-id="ca2a6-131">You can enable or disable your plugins at any time in the Unreal Editor.</span></span> <span data-ttu-id="ca2a6-132">Подключаемые модули могут добавлять функциональные возможности в игровой процесс среды выполнения, изменять встроенные возможности подсистемы, создавать новые типы файлов и расширять возможности редактора.</span><span class="sxs-lookup"><span data-stu-id="ca2a6-132">Plugins can add runtime gameplay functionality, modify built-in Engine features, create new file types, and extend the capabilities of the Editor.</span></span>

<!-- ## Engine modifications -->

