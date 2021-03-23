---
title: Общие рекомендации
description: Следите за актуальными рекомендациями по разработке приложений смешанной реальности с помощью Unreal Engine.
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, расширения редактора, редактор Unreal, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, документация, руководства, функции, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, перенос, обновление
ms.openlocfilehash: 478ae3137fc73d1ef516087618ab0247f2164c02
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "98584906"
---
# <a name="general-best-practices"></a>Общие рекомендации

Ниже приведен ряд общих рекомендаций, которые мы советуем соблюдать всем разработчикам при создании проектов Unreal Engine для смешанной реальности.

## <a name="constructors"></a>Конструкторы

Если вам нужен аналог конструктора для схем, используйте [скрипт конструирования](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html) Unreal. Основное его преимущество по сравнению с событиями BeginPlay заключается в том, что скрипт конструктора также выполняется внутри редактора. В большинстве случаев значения могут кэшироваться прямо при запуске или даже во время компиляции.

> [!NOTE]
> Дополнительные сведения о скриптах конструировании см. в [обзоре расширений для редактора](unreal-editor-extensions.md#construction-scripts).

## <a name="3d-buttons-and-textures"></a>Трехмерные кнопки и текстуры

При создании или планировании трехмерных кнопок для применения в приложениях смешанной реальности вполне логично учитывать их влияние на производительность. Но не для каждого объекта необходимо применять пространственные сетки, чтобы он воспринимался объемным. Вы можете использовать объект Paper2D со специальными текстурами, чтобы получить видимость трехмерности. Этот подход особенно хорош для кнопок, которые только кажутся трехмерными, а по сути являются плоским изображением, нанесенным на объект Quad. Более сложная версия такого объекта называется [спрайтом](https://docs.unrealengine.com/AnimatingObjects/Paper2D/Sprites/index.html).

## <a name="variants"></a>Варианты

Используйте [варианты Unreal](https://docs.unrealengine.com/Basics/Levels/Variants/index.html) в тех случаях, когда вы во время выполнения создаете сцену с несколькими конфигурациями объектов. Варианты могут определять изменения для материалов или сеток. 

## <a name="animation"></a>Анимация

Воспользуйтесь преимуществами компонента [сплайн](https://docs.unrealengine.com/API/Runtime/Engine/Components/USplineComponent/index.html) (не путайте его с компонентом "сетка" в сплайне) и [узлов временной шкалы](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Timelines/index.html), если вам нужно создать много анимированных элементов с возможностью взаимодействия. 

<!-- You can find a comprehensive [video tutorial here](https://www.youtube.com/watch?v=bWXI91FdMtk&ab_channel=DoubleCrossGames). -->

## <a name="communications"></a>Коммуникации

Используйте [схему уровня](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Types/LevelBlueprint/index.html), если возникают проблемы с динамическим поиском объектов или слишком велика нагрузка на механизмы взаимодействия между несколькими субъектами и схемами. Не забывайте, что Unreal Engine 4 отличается от Unity и не требует включать все содержимое в компоненты. Схемы уровней — это вполне допустимый и даже рекомендуемый подход, позволяющий упростить обмен данными между несколькими субъектами. Можно даже кэшировать ссылки на объекты при запуске сцены, используя событие OnBeginPlay в схеме уровня.

## <a name="global-state"></a>Глобальное состояние

Вам часто придется хранить состояние для конкретного уровня, например текущие результаты, данные об уровне и отдельных игроках, или что-то еще, что нельзя привязать к конкретному объекту. Не забывайте о возможностях [GameMode](https://docs.unrealengine.com/en-US/InteractiveExperiences/Framework/GameMode/index.html). Большинство разработчиков не подозревают об этой возможности, но GameMode можно создавать отдельно для каждого уровня, чтобы хранить относящиеся к этому уровню данные.

## <a name="optimizing-blueprints"></a>Оптимизация схем

Если ваши схемы работают слишком медленно, не спешите сразу писать новый код на C++, а попробуйте сделать их более "родными" для Unreal. Попробуйте применить автоматический механизм [нативизации](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/TechnicalGuide/NativizingBlueprints/index.html), прежде чем создавать собственное решение.

![Окно применения метода нативизации для настройки схем, где выделен элемент для включения](images/unreal-general-practices-img-01.jpg)
