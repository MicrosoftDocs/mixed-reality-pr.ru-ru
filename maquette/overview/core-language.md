---
title: Ядро языка
description: Узнайте о основных сведениях о языке Макуетте.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Макуетте, создание прототипов, Смешанная реальность, виртуальная реальность, VR, MR, обратная связь, центр обратной связи, ошибки
ms.openlocfilehash: e0c0b2f204aa32245cc13aff4c64fa641313de51
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935627"
---
# <a name="maquettescript-core-language-details"></a><span data-ttu-id="674c8-104">Сведения о языке Макуеттескрипт Core</span><span class="sxs-lookup"><span data-stu-id="674c8-104">MaquetteScript core language details</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->
<span data-ttu-id="674c8-105">![](../images/MaquetteIcon.png)Сведения о базовом языке макуетте Logo макуеттескрипт</span><span class="sxs-lookup"><span data-stu-id="674c8-105">![Maquette logo](../images/MaquetteIcon.png) MaquetteScript Core Language Details</span></span>

## <a name="accessing-maquette-object-and-namespace"></a><span data-ttu-id="674c8-106">Доступ к `Maquette` объекту и пространству имен</span><span class="sxs-lookup"><span data-stu-id="674c8-106">Accessing `Maquette` Object and Namespace</span></span>

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
<span data-ttu-id="674c8-107">Макуетте предоставляет внутренние объекты и интерфейсы JavaScript через `Maquette` объект и его дочерние элементы.</span><span class="sxs-lookup"><span data-stu-id="674c8-107">Maquette exposes internal objects and interfaces in JavaScript through the `Maquette` object and its children.</span></span> <span data-ttu-id="674c8-108">Эта функция описана в документации по [объекту макуетте и пространству имен](https://www.maquette.ms/doc_staging/objects/Maquette.html) .</span><span class="sxs-lookup"><span data-stu-id="674c8-108">This functionality is described in the [Maquette Object and Namespace](https://www.maquette.ms/doc_staging/objects/Maquette.html) documentation.</span></span> 

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
<span data-ttu-id="674c8-109">`Maquette`Объект содержит функции верхнего уровня, чтобы упростить взаимодействие с макуетте и упростить решение повторяющихся проблем.</span><span class="sxs-lookup"><span data-stu-id="674c8-109">The `Maquette` object has top-level functions to make it easier to interact with Maquette itself and make repetitive problems easier to solve.</span></span> <span data-ttu-id="674c8-110">Это описано в документации по [макуеттескриптобжект](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html).</span><span class="sxs-lookup"><span data-stu-id="674c8-110">This is described in the documentation of [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html).</span></span>

## <a name="maquette-startup-and-loading"></a><span data-ttu-id="674c8-111">Запуск и загрузка макуетте</span><span class="sxs-lookup"><span data-stu-id="674c8-111">Maquette Startup and Loading</span></span>

<!-- TODO(Stefan): Need context on why this is important for users and how they will take advantage of this in production? -->
<span data-ttu-id="674c8-112">Макуетте будет загружать и оценивать определенные файлы JavaScript для включения конфигурации, установки и инициализации в следующие моменты времени:</span><span class="sxs-lookup"><span data-stu-id="674c8-112">Maquette will load and evaluate specific JavaScript files to enable config, setup and initialization at the following times:</span></span>

<span data-ttu-id="674c8-113">Во время запуска Макуетте:</span><span class="sxs-lookup"><span data-stu-id="674c8-113">During Maquette startup:</span></span>
<pre>
~/Documents/Maquette/Scripts/OnMaquetteStartup.mqjs
</pre>

<span data-ttu-id="674c8-114">Каждый раз, когда загружается любой проект:</span><span class="sxs-lookup"><span data-stu-id="674c8-114">Whenever any project is loaded:</span></span>
<pre>
~/Documents/Maquette/Scripts/OnMaquetteProjectLoad.mqjs
</pre>

<span data-ttu-id="674c8-115">Проекты загружают свои соответствующие сценарии проекта:</span><span class="sxs-lookup"><span data-stu-id="674c8-115">Projects load their respective project scripts:</span></span>
<pre>
~/Documents/Maquette/Project/&lt;Your Project&gt;/Scripts/OnLoad.mqjs
</pre>

## <a name="javascript-implementation"></a><span data-ttu-id="674c8-116">Реализация JavaScript</span><span class="sxs-lookup"><span data-stu-id="674c8-116">JavaScript Implementation</span></span>

<!-- TODO(Stefan): Is there anything else we can tell users about the JS interpreter as applied to Maquette? -->
<span data-ttu-id="674c8-117">Интерпретатор JavaScript, используемый в Макуетте, основан на [жинт](https://github.com/sebastienros/jint).</span><span class="sxs-lookup"><span data-stu-id="674c8-117">The JavaScript interpreter used in Maquette is based on [Jint](https://github.com/sebastienros/jint).</span></span> <span data-ttu-id="674c8-118">Жинт совместим с ECMAScript 5,1 и поддерживает дополнительные [расширения из ECMAScript 6](https://github.com/sebastienros/jint/issues/343).</span><span class="sxs-lookup"><span data-stu-id="674c8-118">Jint is ECMAScript 5.1 compatible and supports additional [extensions from ECMAScript 6](https://github.com/sebastienros/jint/issues/343).</span></span> 

<span data-ttu-id="674c8-119">Расширение `.mqjs` используется для различения макуетте файлов JavaScript от обычных сценариев JavaScript.</span><span class="sxs-lookup"><span data-stu-id="674c8-119">The extension `.mqjs` is used to distinguish Maquette javascript files from normal JavaScript.</span></span>

## <a name="see-also"></a><span data-ttu-id="674c8-120">См. также</span><span class="sxs-lookup"><span data-stu-id="674c8-120">See also</span></span> 
<!-- TODO(Stefan): Add any additional JS related links that may help with troubleshooting or issues? -->