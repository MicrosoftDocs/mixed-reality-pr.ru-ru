---
title: Обновление приложений SteamVR для Windows Mixed Reality
description: рекомендации по обновлению приложения стеамвр для обеспечения максимальной совместимости с Windows Mixed Reality гарнитурами.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: стеамвр, совместимость, перенос, HoloLens 1-го поколения, гарнитура смешанной реальности, гарнитура windows mixed reality, миграция, Windows 10, Steam, контроллеры движения, хаптикс
ms.openlocfilehash: ee72994691970a3701ec8462ab0f42b6d1da1820589ca68a92c9a78fe1c18a41
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196194"
---
# <a name="updating-steamvr-apps-for-windows-mixed-reality"></a>Обновление приложений SteamVR для Windows Mixed Reality

мы советуем разработчикам тестировать и оптимизировать свои стеамврные возможности для работы на гарнитурах Windows Mixed Reality. В этой документации рассматриваются распространенные улучшения, которые можно сделать, чтобы вы могли работать с Windows Mixed Reality.

## <a name="initial-setup-instructions"></a>Инструкции по начальной настройке

чтобы начать тестирование игры или приложения на Windows Mixed Reality, обязательно ознакомьтесь с нашим [руководством по началу работы.](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)

## <a name="controller-models"></a>Модели контроллеров

1. Если приложение подготавливает модели контроллеров:
    * использование [моделей контроллеров движения Windows Mixed Reality](../../design/motion-controllers.md#rendering-the-motion-controller-model)
    * Используйте Ивррендермодел:: Жеткомпонентстате для получения локальных преобразований в части компонентов (например, указатель a).
2. Опыт, имеющий понятие правой или левой, должен получать подсказки от входных API-интерфейсов для различения контроллеров [(пример Unity)](../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) .

## <a name="controls"></a>Элементы управления

При проектировании или настройке макета элемента управления учитывайте следующий набор зарезервированных команд:
1. Щелчок **левого и правого аналогового стика** зарезервировано для **панели мониторинга Steam**.

> [!NOTE]
> Если вы используете контроллер HP REVERB G2, то нажатие правой кнопки меню зарезервировано для **панели мониторинга Steam**.

2. **кнопка Windows** всегда будет возвращать пользователей Windows Mixed Reality домашней странице.

если это возможно, по умолчанию на основе аналогового стика в соответствии с [Windows Mixed Reality домашней почтовым](../../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) портом

## <a name="tooltips-and-ui"></a>Подсказки и пользовательский интерфейс

Многие игры VR используют преимущества всплывающих подсказок и наложения контроллера движения для обучения пользователей приложениям или играм наиболее важным командам. при настройке приложения для Windows Mixed reality рекомендуется проверить эту часть работы, чтобы убедиться, что всплывающие подсказки сопоставлены с моделями контроллеров Windows.

кроме того, при наличии каких бы то ни было точек в вашем интерфейсе, в которых отображаются образы контроллеров, необходимо предоставить обновленные образы с помощью Windows Mixed Reality контроллеров движения.

## <a name="haptics"></a>хаптикс

начиная с [обновления Windows 10 за апрель 2018](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)г., хаптикс теперь поддерживаются для стеамврного взаимодействия на Windows Mixed Reality. если ваше приложение или игра стеамвр уже включает поддержку хаптикс, теперь она должна работать (без дополнительной работы) с [Windows Mixed Reality контроллерами движения](../../design/motion-controllers.md).

Windows Mixed Reality контроллеры движения используют стандартный мотор хаптикс, а не линейные исполнители, находящиеся в некоторых других стеамврных контроллерах движения. Это может привести к слегка отличающимся впечатлениям от ожидаемого взаимодействия с пользователем. поэтому мы рекомендуем тестировать и настраивать структуру хаптикс с помощью Windows Mixed Reality контроллеров движения. например, иногда короткие хаптик импульсы (5-10 мс) менее заметны на Windows Mixed Reality контроллерах движения. Чтобы получить более заметный импульс, поэкспериментируйте с отправкой более длительного "щелчка" (40-70 мс), чтобы придать мотору больше времени, прежде чем отключать его.

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a>запуск приложений стеамвр из меню Windows Mixed Reality

для функций VR, распространяемых через Steam, мы [обновили Windows Mixed Reality для стеамвр](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) вместе с последними [выпусками Windows](https://insider.windows.com). заголовки стеамвр теперь отображаются в меню Windows Mixed Reality в списке "все приложения" автоматически.

## <a name="windows-mixed-reality-logo"></a>эмблема Windows Mixed Reality

чтобы отобразить Windows Mixed Reality поддержки для вашего заголовка, перейдите на ссылку "изменить страницу хранилища" на целевой странице приложения, выберите вкладку "основные сведения" и прокрутите вниз до пункта "виртуальная реальность". снимите флажок "скрыть Windows Mixed Reality", а затем опубликуйте его в хранилище.

## <a name="bugs-and-feedback"></a>Ошибки и отзывы

ваш отзыв не будет ценным, когда дело доходит до улучшения Windows Mixed Reality стеамвр. отправьте все отзывы и ошибки с помощью [Центр отзывов о Windows](/windows/mixed-reality/enthusiast-guide/filing-feedback). Ниже приведены некоторые [советы о том, как сделать отзыв стеамвр как можно более удобным](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr).

Если у вас есть вопросы или комментарии для совместного использования, вы также можете связаться с нами на нашем [форуме Steam](https://steamcommunity.com/app/719950/discussions/).

## <a name="faqs-and-troubleshooting"></a>Часто задаваемые вопросы и устранение неполадок

Если у вас возникли общие проблемы с настройкой или воспроизведением опыта, [Ознакомьтесь с последними действиями по устранению неполадок](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr).

## <a name="see-also"></a>См. также статью

* [Установка средств](../install-the-tools.md)
* [Журнал драйверов контроллера гарнитуры и движения](/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [Windows Mixed Reality минимальные рекомендации по совместимости оборудования пк](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)