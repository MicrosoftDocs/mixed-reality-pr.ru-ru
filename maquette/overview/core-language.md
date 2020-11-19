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
# <a name="maquettescript-core-language-details"></a>Сведения о языке Макуеттескрипт Core

<!-- TODO(Harrison): Need consolidated logo with text -->
![](../images/MaquetteIcon.png)Сведения о базовом языке макуетте Logo макуеттескрипт

## <a name="accessing-maquette-object-and-namespace"></a>Доступ к `Maquette` объекту и пространству имен

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
Макуетте предоставляет внутренние объекты и интерфейсы JavaScript через `Maquette` объект и его дочерние элементы. Эта функция описана в документации по [объекту макуетте и пространству имен](https://www.maquette.ms/doc_staging/objects/Maquette.html) . 

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
`Maquette`Объект содержит функции верхнего уровня, чтобы упростить взаимодействие с макуетте и упростить решение повторяющихся проблем. Это описано в документации по [макуеттескриптобжект](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html).

## <a name="maquette-startup-and-loading"></a>Запуск и загрузка макуетте

<!-- TODO(Stefan): Need context on why this is important for users and how they will take advantage of this in production? -->
Макуетте будет загружать и оценивать определенные файлы JavaScript для включения конфигурации, установки и инициализации в следующие моменты времени:

Во время запуска Макуетте:
<pre>
~/Documents/Maquette/Scripts/OnMaquetteStartup.mqjs
</pre>

Каждый раз, когда загружается любой проект:
<pre>
~/Documents/Maquette/Scripts/OnMaquetteProjectLoad.mqjs
</pre>

Проекты загружают свои соответствующие сценарии проекта:
<pre>
~/Documents/Maquette/Project/&lt;Your Project&gt;/Scripts/OnLoad.mqjs
</pre>

## <a name="javascript-implementation"></a>Реализация JavaScript

<!-- TODO(Stefan): Is there anything else we can tell users about the JS interpreter as applied to Maquette? -->
Интерпретатор JavaScript, используемый в Макуетте, основан на [жинт](https://github.com/sebastienros/jint). Жинт совместим с ECMAScript 5,1 и поддерживает дополнительные [расширения из ECMAScript 6](https://github.com/sebastienros/jint/issues/343). 

Расширение `.mqjs` используется для различения макуетте файлов JavaScript от обычных сценариев JavaScript.

## <a name="see-also"></a>См. также 
<!-- TODO(Stefan): Add any additional JS related links that may help with troubleshooting or issues? -->