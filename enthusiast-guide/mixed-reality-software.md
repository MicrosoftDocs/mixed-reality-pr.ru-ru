---
title: Обзор программного обеспечения смешанной реальности и история выпусков
description: Обзор основных программных компонентов для Windows Mixed Reality и их истории выпусков
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Смешанная реальность, виртуальная реальность, VR, MR, программные компоненты, журнал выпусков, заметки о выпуске, журнал версий
appliesto:
- Windows 10
ms.openlocfilehash: 76a913ae5890c908dda4e25d5b5c21554fdae7f0
ms.sourcegitcommit: 9c88703a832fb8ca8476e808499d06239ea5d2cd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/13/2020
ms.locfileid: "92011427"
---
# <a name="mixed-reality-software-overview-and-release-history"></a>Обзор программного обеспечения смешанной реальности и история выпусков

## <a name="introduction-to-mixed-reality-software"></a>Введение в программное обеспечение для смешанной реальности

Windows Mixed Reality состоит из следующих основных программных компонентов:

1. **Портал смешанной реальности**, предоставляющий основной интерфейс Windows Mixed Reality
    * В Windows 10 версии 1709 и 1803 портал Mixed Reality является ключевым компонентом операционной системы Windows 10 и обновляется с помощью Центр обновления Windows.
    * В Windows 1809 10 портал смешанной реальности обновляется с помощью Microsoft Store приложения.
2. **Пакет по запросу "функция смешанной реальности** " (FOD) автоматически загружается и устанавливается во время первого запуска портала смешанной реальности. Дополнительные сведения о пакете FOD можно найти [здесь](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality) .
3. **Драйвер наушников и контроллеров движения в смешанной реальности**, также называемый драйвером датчиков HoloLens, является пакетом драйверов, который позволяет гарнитурам Windows Mixed Reality работать с Windows Mixed Reality. Он автоматически скачивается и устанавливается с помощью Центр обновления Windows при первом подключении гарнитуры смешанной реальности и регулярно обновляется с помощью Центр обновления Windows
4. **Драйверы модели контроллера движения смешанной реальности** содержат трехмерные модели контроллеров движения смешанной реальности, необходимые для работы в смешанной реальности. Это автоматически скачивается и устанавливается с помощью Центр обновления Windows при первом подключении контроллеров движения смешанной реальности к компьютеру и обновления с помощью Центр обновления Windows
5. **Windows 10, версия 1709 (обновление создателя отправителя) или более поздней версии** , содержит ключевые компоненты ОС и технологии, обеспечивающие использование Windows Mixed Reality.

Кроме того, для использования Windows Mixed Reality в Стеамвр требуется следующее программное обеспечение:

6. **Стеамвр**, разработанная и обслуживаемая корпорацией вентилей, которая позволяет приложениям и играм Virtual Reality на Steam. Дополнительные сведения можно найти [здесь](https://go.microsoft.com/fwlink/?linkid=862788)
7. Компонент **Windows Mixed Reality для стеамвр** , который связывает Стеамвр с Windows Mixed Reality. Дополнительные сведения об этом компоненте можно найти [на странице Windows Mixed Reality для стеамвр](http://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

Управление гарнитурой Windows Mixed Reality:

8. **Вспомогательное приложение для устройств**, разработанное и обслуживаемое каждым производителем гарнитуры, предоставляет краткое введение в гарнитуру Windows Mixed Reality. На гарнитурах со встроенными возможностями Bluetooth приложение-помощник для устройств позволяет восстанавливать контроллеры движения в их связывание с фабрикой Bluetooth. Некоторые гарнитуры (например, Samsung Одиссэй и Samsung Одиссэй +) также используют приложение "помощник по устройствам" для предоставления обновлений встроенного по в гарнитуру от производителя гарнитуры. Это приложение скачивается автоматически при первом подключении гарнитуры и может быть найдено в меню "Пуск" Windows.

## <a name="windows-10-release-notes---may-2020"></a>Заметки о выпуске Windows 10 — Май 2020

**Обновление Windows 10 май 2020 (v2004)** включает новые функции для головных телефонов Windows Mixed Reality (VR), например возможность запуска приложений Win32 на домашней странице смешанной реальности. HoloLens (1-й общий) находится в долгосрочном обслуживании (LTS), а обновления обслуживаются ежемесячно.

Чтобы выполнить обновление до последней версии на компьютере для головных телефонов Windows Mixed Reality (VR), откройте приложение **параметров** , перейдите в раздел **Обновление & безопасность**, а затем нажмите кнопку **проверить наличие обновлений** . На компьютере с Windows 10 можно также вручную установить **Обновление Windows 10 2020** с помощью [средства создания Windows Media](https://www.microsoft.com/software-download/windows10).

**Последний выпуск для Desktop**: Windows 10 v2004 (10.0.19041.264)

### <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>Обновления для впечатляющих головных телефонов Windows Mixed Reality

#### <a name="introducing-the-new-microsoft-edge"></a>Знакомство с новым Microsoft ребром
Как [было объявлено ранее](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge), мы внесли обновления для лучшей поддержки с помощью нового браузера Microsoft ребра в Windows Mixed Reality. Новая версия Microsoft посвящена внедрению проекта Chromium с открытым исходным кодом для создания лучшей веб-совместимости для клиентов и менее фрагментации веб-приложений для всех веб-разработчиков. Он также поддерживает Вебкср, новый стандарт для создания впечатляющих веб-приложений для головных телефонов VR вместо Вебвр.

#### <a name="improved-settings-for-wmr"></a>Улучшенные параметры для ВМР
Благодаря вашим отзывам мы добавили и рассмотрели параметры на странице экрана гарнитуры:

* **Визуальное качество моего дома** . изменение этих параметров влияет только на домашнюю среду Mixed Reality (Клифф House и скилофт):

* **Настройте уровень детализации и качество влияния на домашней странице смешанной реальности** . Это изменяет некоторые изменения, которые повлияют на использование в домашней среде. В частности, визуальное качество различных материалов (деревянное, конкретное и т. д.) будет масштабироваться по мере изменения этого параметра с низкой на высокий.

* **Изменение разрешения окна приложения** . по умолчанию большинство 2D-окон, запущенных в домашней системе, запускаются с разрешением 720p. Хотя можно вручную изменить размер горизонтально & по вертикали, можно также разрешить их запуск в режиме 1080p. Ранее этот параметр был доступен в качестве высококачественного (бета-версии) в режиме визуального качества. Теперь мы соответствующим образом разделием его как отдельный параметр.

* **Параметры работы** . Эти параметры позволяют настроить режим смешанной реальности, чтобы снизить нагрузку на системы, в которых оборудование может столкнуться с неограниченным 90 кадрами/с. Вы можете явно включить или отключить эти дополнительные параметры или выбрать параметр Разрешить Windows принять и позволить нашим эвристическим вариантам продолжить выбор между включением и отключением.

* **Решение** . Если у вас есть гарнитура высокого разрешения, как и в случае с переглаголом HP, мы поддерживаем ее запуск в собственном разрешении или с меньшим разрешением по соображениям производительности. Более ранние гарнитуры, такие как Samsung Одиссэй и Одиссэй +, поддерживают только одно разрешение, поэтому вы не сможете изменить этот параметр на этих гарнитурах.

* **Частота кадров** . Теперь можно вручную задать частоту кадров для экрана гарнитуры или продолжить, чтобы позволить Windows использовать его эвристику, чтобы определить, подходит ли 60 гц или 90 Гц.

* **Калибровка** . как и раньше, вы можете настроить IPD (интерпупиллари distance), если это поддерживается вашей гарнитурой.

* **Переключение ввода** . переключить поведение переключения фокуса ввода (Win + Y) в автоматический режим (на основе отзывов датчика присутствия) или вручную.

#### <a name="new-cortana-app"></a>Новое приложение Кортаны
Это обновление для Windows включает в себя последнюю версию приложения Кортаны, которая в настоящее время доступна только для английского языка (США) и больше не поддерживает некоторые специальные команды, такие как «взять изображение» и «взять видео». Вы по-прежнему сможете использовать новую команду Кортаны для запуска приложений, а также новые команды для повышения производительности, такие как: «когда мое следующее собрание?» или «отправить сообщение электронной почты с <name> опозданием».
    
#### <a name="additional-updates-in-available-in-19041546-released-october-2020"></a>Дополнительные обновления в версии 19041,546 (выпущены 2020 октября)
Ежемесячное обновление для обслуживания настольных систем включает следующие изменения для устройств Windows Mixed Reality. 
* Уменьшает искажения и аберратионс в подключенных к головке Windows Mixed Reality выдисплеях (ХМД). 
* Добавлена поддержка предстоящих контроллеров движения HP Windows Mixed Reality. 
* Изменяет поведение параметра частоты обновления 90Hz в Windows Mixed Reality, чтобы оно больше не было автоматически переключаться на 60 Гц в некоторых случаях, когда не удается достигнуть 90Hz. 

#### <a name="please-help-us-improve"></a>Помогите нам улучшить!
Мы постоянно будем искать улучшения совместимости.  Если вы нашли в Windows Mixed Reality избранное приложение Win32, которое работает неправильно, отправьте отзыв через наш [центр обратной связи](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub).

### <a name="prior-release-notes"></a>Заметки о предыдущем выпуске

* [Заметки о выпуске — 2019 мая](release-notes-may-2019.md)
* [Заметки о выпуске — октябрь 2018 г.](release-notes-october-2018.md)
* [Заметки о выпуске — 2018 апреля](release-notes-april-2018.md)
* [Заметки о выпуске — октябрь 2017 г.](release-notes-october-2017.md)
* [Заметки о выпуске — август 2016 г.](release-notes-august-2016.md)
* [Заметки о выпуске — май 2016 г.](release-notes-may-2016.md)
* [Заметки о выпуске — март 2016 г.](release-notes-march-2016.md)

## <a name="mixed-reality-headset-and-motion-controller-driver-release-history"></a>Журнал выпусков гарнитуры и драйвера контроллера движения смешанной реальности ###

Этот драйвер автоматически скачивается и устанавливается с помощью Центр обновления Windows, но ссылки для скачивания предоставляются в виде встроенных:

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10, версия 2004 (2020 мая Update) ####

   | Версия          | Дата выпуска          | Основные изменения                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102156)  | 8 октября, 2020  | Совместимость с Windows 10, версия 1903 и более поздние версии.<br/><ul><li>Официальная поддержка для переглагола, HP Омницепт и нового контроллера HP.</li><li>Незначительные изображения для переглагола HP и Samsung Одиссэй +. (Требуется [Сборка ос 19041,546](https://support.microsoft.com/en-us/help/4577063/windows-10-update-kb4577063) или более поздней версии или [сборки ос 18362,1110 и 18363,1110](https://support.microsoft.com/en-us/help/4577062/windows-10-update-kb4577062) или более поздней версии).</li><li>Улучшения состояния электропитания компьютера в спящем режиме для уменьшения числа ошибок свв 1-4.</li><li>Небольшие исправления и надежность на платформе гарнитуры Windows Mixed Reality.|
   | [10.0.19041.1009](https://www.microsoft.com/en-us/download/details.aspx?id=101260)  | 7 мая, 2020      | Совместимость с Windows 10, версия 1903 и более поздние версии.<br/><ul><li>Небольшие исправления и надежность на платформе гарнитуры Windows Mixed Reality.</li></ul>  |

#### <a name="windows-10-version-1903-may-2019-update"></a>Windows 10, версия 1903 (2019 мая Update) ####

   | Версия          | Дата выпуска          | Основные изменения                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.18362.1162](https://www.microsoft.com/en-us/download/details.aspx?id=100421)  | Октябрь 14, 2019      | Совместимость с Windows 10, версия 1809 и более поздние версии.<br/><ul><li>Небольшие исправления для головной платформы Windows Mixed Reality.</li></ul>  | 
   | [10.0.18362.1062](https://www.microsoft.com/en-us/download/details.aspx?id=58492)  | Июнь 24, 2019      | Совместимость с Windows 10, версия 1809 и более поздние версии.<br/><ul><li>Высококачественная платформа Windows Mixed Reality и улучшения надежности вокруг спящих компьютеров и переходов между состояниями электропитания.</li></ul>  | 
   | [10.0.18362.1024](https://www.microsoft.com/en-us/download/details.aspx?id=58225)  | 1 мая 2019 г.      | Совместимость с Windows 10, версия 1809 и более поздние версии.<br/><ul><li>Содержит обновления встроенного по для стоек 2017, ASUS, Dell, Fujitsu, HP, Lenovo и медион Windows Mixed Reality. Это обновление встроенного по улучшает совместимость и надежность интерфейса гарнитуры с помощью определенных графических адаптеров и графических драйверов.</li><li>Усовершенствования на платформе и надежности гарнитуры Windows Mixed Reality</li></ul>  | 

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, версия 1803 (обновление от апреля 2018) и версия 1809 (обновление за Октябрь 2018 г.) ####

   | Версия          | Дата выпуска          | Основные изменения                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17763.1069](https://www.microsoft.com/en-us/download/details.aspx?id=57702)  | 2 января 2019 г.      | Совместимость с Windows 10, версия 1803 и более поздние версии.<br/><ul><li>Исправления колебаний перебои и исправлений для головного телефона</li><li>Исправления надежности режима фонарик</li></ul>  | 
   | [10.0.17760.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57358)  | 1 октября, 2018      | Первоначальный общедоступный выпуск драйвера для Windows 10, версия 1809.<br/>Совместимость с Windows 10, версия 1803 и более поздние версии.<br/><ul><li>Включает новые функции Windows Mixed Reality, такие как режим фонарик, в Windows 10, версия 1809</li><li>Улучшения в отслеживании и надежности гарнитуры</li><li>Улучшение отслеживания и повышения производительности контроллера движения</li><li>Производительность и улучшения USB</li></ul>  | 
   | [10.0.17134.1004](https://www.microsoft.com/en-us/download/details.aspx?id=56845)  | Апрель 27, 2018      | Первоначальный общедоступный выпуск драйвера для Windows 10, версия 1803<br/> <ul><li>Улучшения в отслеживании и надежности гарнитуры</li><li>Улучшение отслеживания и повышения производительности контроллера движения</li></ul>  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10, версия 1709 (с обновлениями для дизайнеров) ####

   | Версия          | Дата выпуска          | Основные изменения                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16299.1070](https://www.microsoft.com/en-us/download/details.aspx?id=56571)  | 6 февраля, 2018    | <ul><li>Официальная поддержка гарнитуры смешанной реальности 3Glasses Блубур S2</li></ul> |
   | [10.0.16299.1062](https://www.microsoft.com/en-us/download/details.aspx?id=56332)  | 19 декабря 2017 г.   | <ul><li>Устраняет проблему с HID, приводящую к тому, что на некоторых компьютерах *произошла* ошибка с кодом 2181038087-7</li><li>Различные исправления стабильности и надежности</li></ul> |
   | [10.0.16299.1058](https://www.microsoft.com/en-us/download/details.aspx?id=56277)  | 5 декабря 2017 г.    | <ul><li>Улучшенная функция отслеживания головного телефона</li><li>Улучшения скорости реагирования сенсорного контроллера движения</li><li>Устраняет проблему, при которой иногда может произойти сбой установки драйвера.</li><li>Различные исправления стабильности и надежности</li></ul> |
   | [10.0.16299.1042](https://www.microsoft.com/en-us/download/details.aspx?id=56265)  | 21 ноября 2017 г.   | <ul><li>Разрешает проблему, которая привела к подаче на экран гарнитуры, иногда при ее использовании</li><li>Устраняет проблему, которая иногда может приводить к появлении контроллеров движения</li><li>Улучшения производительности датчика присутствия для гарнитуры гипервизора Dell</li><li>Различные исправления стабильности и надежности</li></ul> |
   | 10.0.16299.1036  | 7 ноября 2017 г.    | <ul><li>Улучшения механику, повышающие подачу контроллера движения:<ul><li>Теперь скорость будет передаваться правильно, если точность расположения приблизительна, так что теперь можно порождать вызов за пределами головного компьютера!</li><li>Пример кода для вызова можно найти в пакете Unity "Сровингстартер" [здесь](https://github.com/keluecke/MixedRealityToolkit-Unity/tree/master/External/Unitypackages/). Откройте сцену создания сцены, чтобы начать работу</li></ul></li><li>Улучшенный отчет о батарее контроллера движения</li><li>Различные исправления стабильности и надежности</li></ul> |
   | 10.0.16299.1012  | Октябрь 17, 2017    | Первоначальный общедоступный выпуск драйвера                              |

### <a name="mixed-reality-motion-controller-model-driver-release-history"></a>Журнал выпусков драйвера контроллера движения смешанной реальности ###

Этот драйвер также автоматически скачивается и устанавливается с помощью Центр обновления Windows, но ссылки для скачивания предоставляются в виде встроенных:

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10, версия 2004 (2020 мая Update)

| Версия          | Дата выпуска          | Основные изменения                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102155)  | 16 сентября, 2020      | Первоначальный общедоступный выпуск драйвера для новых контроллеров Motion HP. Совместимость с Windows 10, версия 1903 и более поздние версии. Этот драйвер совместим только с новыми контроллерами Motion HP.  |

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, версия 1803 (обновление от апреля 2018) и версия 1809 (обновление за Октябрь 2018 г.) ####

   | Версия          | Дата выпуска          | Основные изменения                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17737.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57359)  | 1 октября, 2018      | Первоначальный общедоступный выпуск драйвера для Windows 10, версия 1809. Совместимость с Windows 10, версия 1803 и более поздние версии.  |
   | [10.0.17079.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57002)  | Апрель 17, 2018      | Первоначальный общедоступный выпуск драйвера для Windows 10, версия 1803.  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10, версия 1709 (с обновлениями для дизайнеров) ####

   | Версия          | Дата выпуска          | Основные изменения                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16291.1000, 10.0.16299.1012](https://www.microsoft.com/download/details.aspx?id=56414)  | Октябрь 17, 2017    | Первоначальный общедоступный выпуск драйвера                          |

### <a name="mixed-reality-portal-release-history"></a>Журнал выпусков портала смешанной реальности ###

В Windows 1809 10 [портал смешанной реальности](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) обновляется с помощью Microsoft Store приложения.

#### <a name="windows-10-version-1809-and-newer"></a>Windows 10, версия 1809 и более поздние версии ####

   | Версия            | Дата выпуска          | Основные изменения                                                 |
   |--------------------|-----------------------|---------------------------------------------------------------|
   | 2000.20071.1133.0  | 5 августа 2020 г.        | <ul><li>Поддержка [опенкср](https://docs.microsoft.com/windows/mixed-reality/openxr) для приостановки окна предварительного просмотра.</li></ul>  | 
   | 2000.20041.1212.0  | 11 мая 2020 г.          | <ul><li>Устраняет ошибку синхронизации, которая приводит к нестабильной ошибке 15-5.</li><li>Улучшенная поддержка запуска Windows Mixed Reality без подключения к Интернету.</li><li>Улучшенная поддержка связывания контроллеров движения с помощью **настройки контроллеров**.</li></ul>  | 
   | 2000.20031.1202.0  | 14 апреля 2020 г.        | <ul><li>Поддержка регистрации для получения информации, советов и предложений о Windows Mixed Reality.</li></ul>  | 
   | 2000.20011.1312.0  | 11 февраля 2020 г.     | <ul><li>Улучшенная поддержка приложений, использующих [опенкср](https://docs.microsoft.com/windows/mixed-reality/openxr) на устройствах с обновлением 2019 мая.</li><li>Устраняет проблемы специальных возможностей и фокуса клавиатуры</li></ul>  | 
   | 2000.19101.1211.0  | 11 ноября 2019 г.     | <ul><li>Устраняет ошибку, запрещающую переключение визуальных элементов границы комнаты.</li><li>Устраняет ошибку, которая не позволяет центрировать гарнитуру во время настройки границ комнаты.</li></ul>  | 
   | 2000.19081.1301.0  | 23 сентября 2019 г.    | <ul><li>Устраняет проблему, при которой в гарнитурах, вызывающих проблемы с оборудованием, отображалось неправильное сообщение об ошибке. Пользователи, получившие код ошибки 1-4 в предыдущих версиях, теперь могут получить более конкретный код ошибки для своего состояния устройства.</li></ul>  |
   | 2000.19071.1302.0  | 13 августа, 2019     | <ul><li>Поддержка приложений, использующих [опенкср](https://docs.microsoft.com/windows/mixed-reality/openxr) на устройствах с обновлением 2019 мая.</li></ul>  | 
   | 2000.19061.1011.0  | 16 июля 2019 г.         | <ul><li>Поддержка параметров конфигурации JSON для настройки поведения приложения. Дополнительные сведения см https://docs.microsoft.com/windows/mixed-reality/location-based-experiences#setup . в статье.</li></ul>  | 

### <a name="steamvr-release-history"></a>Журнал выпусков Стеамвр ###

Заметки о выпуске вентилей для Стеамвр можно найти здесь: [https://steamcommunity.com/app/250820](https://steamcommunity.com/app/250820)

### <a name="windows-mixed-reality-for-steamvr-release-history"></a>Журнал выпусков Windows Mixed Reality для Стеамвр ###

Заметки о выпуске для компонента Windows Mixed Reality для Стеамвр можно найти здесь: [http://steamcommunity.com/games/719950/announcements/](http://steamcommunity.com/games/719950/announcements/)