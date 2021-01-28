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
# <a name="editor-extensions-in-unreal"></a>Расширения редактора в Unreal

Unreal предоставляет широкий набор возможностей, с помощью которых вы можете настроить систему под ваши требования. Это могут быть как простые и ограниченные возможности, так и очень мощные и сложные. Ниже перечислены шаги в порядке возрастания сложности. Как правило, для решения проблемы сначала нужно попробовать простые решения, а только затем переходить к более сложным. Например, простейший скрипт конструирования в большинстве случаев успешно применим вместо подключаемых модулей. 

<!-- Also, engine modification should be a last resort, as it is not only complex, but integrating changes back into the engine for simple work-around can take a disproportionately long time. -->

## <a name="construction-scripts"></a>Скрипты конструирования

Скрипты конструирования можно использовать для выполнения действий инициализации, которые выполняются при создании экземпляра схемы.

* [Пользовательский скрипт конструирования](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)
* [Пример схемы](https://docs.unrealengine.com/Resources/ContentExamples/Blueprints/1_4/index.html)
* [Видеоруководство](https://www.youtube.com/watch?v=z1SD-d9yJmQ&ab_channel=UnrealEngine)

## <a name="scripted-actions"></a>Заданные действия

Заданные действия — это схемы служебных программ для редактора. Их можно запустить в редакторе Unreal, выполнив следующие действия:
* Щелкните правой кнопкой мыши элемент **Assets** (Активы) в обозревателе содержимого.
* Или щелкните правой кнопкой мыши элемент **Actors** (Субъекты) в окнах просмотра уровня или структуры мира.

Заданные действия идеально подходят для тех случаев, когда логика схемы должна иметь контекстуальные сведения о наборах активов или субъектов. Обычно заданное действие получает список активов или субъектов, которые вы выбрали при запуске этого действия, а затем изменяет эти объекты или включает их в свой граф.

* [Заданные действия](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/ScriptedActions/index.html)
* [Запуск заданных действий при запуске проекта](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/StartupObjects/index.html)

## <a name="editor-utility-widgets"></a>Мини-приложения служебной программы редактора

[Мини-приложения служебной программы редактора](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) удобно использовать, когда нужно добавить новые элементы в пользовательский интерфейс редактора Unreal. Мини-приложения служебной программы редактора основаны на подсистеме UMG (Unreal Motion Graphics), поэтому вы можете настраивать мини-приложения в схеме так же, как и для любой другой схемы мини-приложения UMG.

Эти мини-приложения предназначены специально для пользовательского интерфейса редактора, и с их помощью можно создать настраиваемые вкладки редактора. Затем можно выбрать эти настраиваемые вкладки в меню Windows (как обычные вкладки редактора).

## <a name="plugins"></a>Подключаемые модули

Unreal позволяет разрабатывать собственные пользовательские [подключаемые модули](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html) и управлять ими для применения в средствах и среде выполнения UE4. Вы можете в любое время включить или отключить подключаемые модули в редакторе Unreal. Подключаемые модули могут добавлять функциональные возможности в игровой процесс среды выполнения, изменять встроенные возможности подсистемы, создавать новые типы файлов и расширять возможности редактора.

<!-- ## Engine modifications -->

