---
title: Общие сведения о программировании
description: Узнайте, как получить доступ к объектам и интерфейсам Макуетте с помощью сценариев.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, макуетте, создание прототипов, смешанная реальность, виртуальная реальность, VR, MR, отзыв, центр обратной связи, ошибки
ms.openlocfilehash: 969a4aedb60d947782acb41742b33f275e7c841c1989144b586b0329db3c3b57
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197878"
---
# <a name="programming-overview"></a>Общие сведения о программировании

<!-- TODO(Harrison): Need consolidated logo with text -->

![Эмблема](../images/MaquetteIcon.png) Общие сведения о программировании

Microsoft Макуетте использует JavaScript (ECMAScript 5,1 с расширениями) на основе интерпретатора [жинт](https://github.com/sebastienros/jint) . Расширение `.mqjs` используется для различения макуетте файлов JavaScript от обычных сценариев JavaScript.

<!-- TODO(Stefan): Need more context and high-level explanation of Maquette objects, their accessible interfaces, and functionality. 
                   - What can they do and what problems can they solve?
                   - Is there a specific link to the Maquette object API that can be included here?  
-->
Объекты и интерфейсы макуетте доступны и могут быть написаны с помощью `Maquette` объекта. Документация по объектам и интерфейсам Макуетте приведена в справочнике по API Макуетте.

<!-- TODO(Stefan): Link to roadmap information, which hasn't been documented yet. -->
Макуеттескрипт — это новое сложение и в Flux, поэтому изменения должны быть ожидаемыми. Более подробная документация и обновления доступны в ближайшее время.

<!-- TODO(Stefan): Is Spotlights a component or added functionality of Maquette? -->
## <a name="spotlights-on-scripting"></a>Прожекторы о написании сценариев

* Подлежит внесению в сценарий — прожекторы, посвященные примерам и учебникам
  * 2x Images/Caption — ссылка на страницу Spotlight

<!-- TODO(Stefan): Each of these bullets need to be fleshed out. -->
## <a name="getting-started-with-maquettescript"></a>Начало работы с Макуеттескрипт

* МКЖС и JS
* Модель программирования
  * Сравнение редактирования и запуска
* Ссылка на рабочий процесс программирования
* Ссылка для предоставления общего доступа к результатам

## <a name="programming-workflow"></a>Рабочий процесс программирования

<!-- TODO(Stefan): Which of these bullets are no longer TBD? We only want to include documentation on existing content. -->
TBD
* REPL
* Операция со скриптами
* Операция отладчика
* Цикл отладки
* Копировать/вставить код?

## <a name="running-mqjs-scripts"></a>Выполнение скриптов МКЖС

<!-- TODO(Stefan): Need screenshot -->
Чтобы запустить файл Макуеттескрипт. МКЖС, перейдите к сопутствующим окнам Макуетте и откройте вкладку скрипты, чтобы найти скрипты.

> [!NOTE] 
> Некоторые параметры не будут работать, поскольку не поставляются сценарии.

## <a name="vscode-editor-workflow"></a>Рабочий процесс редактора VSCode

Чтобы оценить сценарий в Макуетте из VSCode, пользователю необходимо получить сведения о двух командах:

   `CTRL-5` Вычисляет выделенный текст или всю строку, в которой находится курсор. 

   `CTRL-SHIFT-5` оценивает весь файл.

<!-- TODO(Stefan): This could use a nice simple infographic of the REPL loop. -->
Текст отправляется в Макуетте, вычисляется в среде JavaScript, а результат отправляется обратно в консоль вывода VSCode. Его можно использовать в качестве REPL (read-eval-print-loop).

## <a name="example-first-step"></a>Пример первого шага

<!-- TODO(Stefan): What kind of file, a C# or .mqjs file? -->
Скопируйте следующий код в файл в VSCode:

```csharp
var myCube = Maquette.CreateCube();
myCube.position = Maquette.User.GetPositionInFront(0.6);
myCube.color = Color(1.0, 0.5, 0.0);
```

<!-- TODO(Stefan): Need screenshot. -->
Выберите код или только разделы и нажмите кнопку `CTRL-5` выполнить. При этом необходимо создать куб, поместить его перед вами и изменить его цвет.

Есть дополнительные примеры для поиска по расширению.

## <a name="sharing-results"></a>Общий доступ к результатам

<!-- TODO(Stefan): Need to fill in content/context for these bullets. If there's a lot of content, we might consider breaking this out into it's own doc. -->
Совместное использование между пользователями и командами
* ZIP-проект в каталоге документов
* Копировать проект в общую папку
* Добавление расположения файлов для отправки общего ресурса команды в группу Макуетте

<!-- TODO(Stefan): Need to break these out into their own sections and fill in the missing content/context. 
                   - Which of these is accessible now and not TBD?
-->
TBD
* Включает ссылку на код в любом расположении с относительными и абсолютными путями, модулями
* Libraries?
* Поддержка времени выполнения
* Неразрешенные внешние-поведение при отсутствии записей или аварийном завершении
* Можно ли добавить/изменить или наблюдать за сценарием, связанным с конкретными объектами?
  * Можно ли скопировать и вставить этот скрипт в другое место?
  * Что насчет свойств объекта?
  * Именование объектов в сцене (Переименование скрипта с помощью сценария)
  * Ключевое слово или SELF для сценария, связанного с объектом
  * Если щелкнуть объект правой кнопкой мыши, можно ли увидеть связанный с ним код (и все его иерархии).
  * Можно ли выбрать пользовательский интерфейс и получить код в VSCode?
  * Хранить код, связанный с объектом "вместе", в исходном файле скрипта?
  * Поместить окно свойств вверх объекта при щелчке? В VR и на главной вкладке?
* Проблемы с безопасностью
* Тестирование — может быть определено, но можно предложить записать видео или кадр по сценарию
* Если у нас есть механизм создания отчетов об ошибках, можно сделать его доступным через сценарий для других (?)... более поздней версии
* Развертывание — как предоставить общий доступ к результату, упаковать как EXE-файл
* Запуск и управление демонстрацией, спектатинг и мониторинг
* Режим проигрывателя
* У нас может быть сегмент, в котором можно сделать "компоненты" для совместного использования? (может быть подлежит определению)
  * Есть #include? Этот механизм обрабатывает чистый JS, но может иметь конфликты пространств имен.
  * Есть ли что-то, что мы можем сделать, чтобы макуетте внедрить некоторые другие макуетте с именованными объектами для сопоставления с кодом JS?
