---
title: Получение справки по совместимости ПК в Windows Mixed Reality
description: Справочный ресурс для проблем совместимости ПК при работе с Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Смешанная реальность, виртуальная реальность, VR, MR, обратная связь, центр обратной связи, ошибки
appliesto:
- Windows 10
ms.openlocfilehash: 75d8ade12d5534a1eb86f36bcdd590539a6811b5
ms.sourcegitcommit: 24d96bf3bb9a3143445e018195edae99d91684c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2020
ms.locfileid: "92683180"
---
# <a name="get-help-with-pc-compatibility-in-windows-mixed-reality"></a>Получение справки по совместимости ПК в Windows Mixed Reality

При настройке Windows Mixed Reality или запуске приложения для [проверки компьютеров Windows Mixed Reality](https://www.microsoft.com/p/windows-mixed-reality-pc-check/9nzvl19n7cnc?rtc=1#activetab=pivot:overviewtab) на компьютере вы получите отчет о готовности компьютера к его запуску. Ниже приведены некоторые сведения о том, что можно увидеть.

Чтобы обеспечить возможность запуска смешанной реальности, ознакомьтесь с [минимальными требованиями к совместимости оборудования для ПК](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).

## <a name="youre-good-to-go"></a>Все готово

Хорошие новости — ваш компьютер может работать под управлением Windows Mixed Reality. Но следует помнить, что между оборудованием и конфигурацией компьютера по-прежнему есть различия, поэтому опыт работы в смешанной реальности может не совпадать на каждом ПК.

## <a name="supports-some-features"></a>Поддерживает некоторые функции

Ваш компьютер должен иметь возможность запускать некоторые возможности Windows Mixed Reality, но может не обеспечивать наилучшее удобство работы. Графика может отставать, некоторые приложения и игры могут работать плохо, и некоторые могут вообще не выполняться. 

Ниже приведены сообщения, которые вы можете увидеть, и что делать с ними:

### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>На этом компьютере имеется Интегрированная графическая карта с одним каналом ОЗУ

Интегрированные графические карты предоставляют лучшие возможности Windows Mixed Reality на компьютерах с двухканальной ПАМЯТЬю. При возникновении проблем с производительностью попробуйте выполнить одно из следующих действий.

* Установите [совместимую дискретную графическую карту](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines).
* Установите дополнительный ОЗУ, чтобы создать двухканальный ОЗУ.
* Переключитесь на [совместимый компьютер](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>На этом компьютере имеется Конфигурация гибридной графики с несовместимой связью PCIe

PCIe означает, что *устройство Interconnect для периферийных компонентов Express* . Это подключение, используемое ПК для связи с графической картой. Конфигурация может работать, но при возникновении проблем необходимо переключиться на [совместимый компьютер](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>Графический драйвер этого компьютера может не работать с Windows Mixed Reality

Если возникли проблемы, попробуйте скачать новый графический драйвер с помощью Центр обновления Windows ( **Параметры запуска > > обновить & безопасность > проверить наличие обновлений** ) — или обратитесь к изготовителю ПК или к веб-сайту производителя видеоплаты.

> [!div class="nextstepaction"]
> [Проверка обновлений](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Если это не сработает, необходимо добавить [совместимую графическую карту](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) или переключиться на [совместимый компьютер](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>Процессор этого компьютера может не работать с Windows Mixed Reality

Процессор этого компьютера может не работать с Windows Mixed Reality, так как у него недостаточно ядер. Если Windows Mixed Reality работает неправильно, замените процессор [совместимым](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) или переключитесь на [совместимый компьютер](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>У этого компьютера может не быть совместимой конфигурации USB

Если возникают проблемы с Windows Mixed Reality, попробуйте выполнить следующие действия.

* Подключите гарнитуру к другому USB-порту, если он доступен.
* Если это не поможет, удалите текущий USB-драйвер компьютера, а затем переустановите драйвер Microsoft:

1. Нажмите кнопку **Пуск** и в поле **поиска** введите "Диспетчер устройств".
2. Выберите **Device Manager** из результатов.
3. Разверните категорию для контроллеров универсальной последовательной шины, просмотрите список устройств и удалите несовместимые драйверы.
    * Если список содержит элемент "расширяемый контроллер узла", в конце имени которого отсутствует "Microsoft", этот драйвер не совместим с Windows Mixed Reality. Его необходимо удалить. Чтобы удалить драйвер, щелкните правой кнопкой мыши устройство в списке и выберите **удалить устройство** . Установите флажок **удалить программное обеспечение драйвера для этого устройства** , а затем выберите **Удалить** .
    * Если список содержит элемент "расширяемый контроллер узла", включающий в себя "Етрон", этот USB-контроллер не совместим с Windows Mixed Reality. Вам потребуется использовать другой USB-порт на компьютере или приобрести другой USB-контроллер узла 3,0.
4. Перезагрузите компьютер.
5. Вернитесь к Device Manager и еще раз нахождение расширяемого элемента контроллера узла. Если теперь в конце имени устройства отображается «Microsoft», то все готово. В противном случае повторите действия по удалению, чтобы удалить все дополнительные версии драйвера, не относящиеся к корпорации Майкрософт.

* Если это не поможет, добавьте USB-карту PCIe на компьютер.

### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>На этом компьютере нет Bluetooth 4,0 для контроллеров

Для контроллеров движения смешанной реальности на некоторых гарнитурах требуется Bluetooth 4,0. Вы по-прежнему можете использовать Windows Mixed Reality с контроллером Xbox или с помощью мыши и клавиатуры. также можно использовать USB-адаптер Bluetooth для подключения контроллеров движения к компьютеру. [См. Рекомендуемые адаптеры](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers"></a>В зависимости от гарнитуры может потребоваться адаптер Bluetooth для использования контроллеров движения.

Некоторые гарнитуры встроены в Bluetooth, чтобы контроллеры могли напрямую связываться с гарнитурами. Для использования контроллеров перемещения на компьютере (или отдельном аппаратном) для других требуется радиомодуль Bluetooth. [См. Рекомендуемые адаптеры](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>На этом компьютере нет USB-порта с самостоятельным питанием

Порт USB 3,0 с самостоятельным питанием необходим для подключения гарнитуры Windows Mixed Reality. Подключите подключенный USB-концентратор 3,0 к ПК и используйте его для подключения гарнитуры.

### <a name="this-pc-should-work-but-youll-have-the-best-experience-with-a-high-performance-intel-processor"></a>Этот компьютер должен работать, но у вас будет лучший опыт работы с высокопроизводительным процессором Intel®

Этот компьютер должен работать, но высокопроизводительный процессор Intel обеспечит оптимальную работу. Мы рекомендуем использовать восьмой процессор с Intel® Core™ или седьмой продукции Intel® Core™ i5.

## <a name="cant-run-windows-mixed-reality"></a>Не удается запустить Windows Mixed Reality

Ниже приведены сообщения, которые вы можете увидеть, и что делать с ними:

### <a name="this-pcs-graphics-card-wont-work-with-windows-mixed-reality"></a>Графическая карта этого компьютера не будет работать с Windows Mixed Reality

Графическая плата этого компьютера несовместима с Windows Mixed Reality. Вам потребуется добавить [совместимую графическую карту](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) или переключиться на [совместимый компьютер](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pcs-graphics-driver-wont-work-with-windows-mixed-reality"></a>Графический драйвер этого компьютера не будет работать с Windows Mixed Reality

Графический драйвер этого компьютера не будет работать с Windows Mixed Reality. Попробуйте загрузить новый графический драйвер с помощью Центр обновления Windows ( **запустите > параметры > обновление & безопасность > проверить наличие обновлений** ). или обратитесь к изготовителю ПК или к веб-сайту производителя видеоплаты. 

> [!div class="nextstepaction"]
> [Проверка обновлений](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Если это не сработает, необходимо добавить [совместимую графическую карту](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) или переключиться на [совместимый компьютер](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pcs-processor-wont-work-with-windows-mixed-reality"></a>Процессор этого компьютера не будет работать с Windows Mixed Reality

Процессор этого компьютера не поддерживает инструкции AVX/Попкнт. Для запуска Windows Mixed Reality необходимо заменить ее на [совместимую графическую карту](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) или переключиться на [совместимый компьютер](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality"></a>На этом компьютере недостаточно свободного дискового пространства для запуска Windows Mixed Reality

Windows Mixed Reality требует 10 ГБ свободного дискового пространства для установки и лучшей производительности. Освободите место на диске и повторите попытку установки.

### <a name="this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality"></a>На этом компьютере работает выпуск Windows, который не поддерживает Windows Mixed Reality

Windows Mixed Reality работает в Windows 10 Домашняя и Windows 10 Pro. Чтобы использовать Windows Mixed Reality, необходимо установить один из этих выпусков.

### <a name="this-pc-isnt-running-the-latest-version-of-windows-10"></a>На этом компьютере не установлена последняя версия Windows 10

Для Windows Mixed Reality требуется обновление Windows 10 Creators Update. [Обновите свой ПК](https://support.microsoft.com/help/4028685) и повторите попытку.

### <a name="this-pc-has-no-usb-30-port"></a>Этот компьютер не имеет порта USB 3,0

Для подключения гарнитуры Windows Mixed Reality потребуется порт USB 3,0. Если вы используете настольный ПК, добавьте USB-карту PCIe. Если вы используете портативный компьютер, необходимо переключиться на [совместимый компьютер](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="you-cant-run-this-app-via-remote-desktop"></a>Невозможно запустить это приложение через удаленный рабочий стол

Для использования Windows Mixed Reality вы будете ПК с подключенным монитором. Если вы используете виртуальную машину или не используете монитор, попробуйте использовать виртуальный адаптер отображения. Это устройство, которое подключается к Дисплайпорту ПК и эмулирует экран компьютера. 

## <a name="getting-the-best-performance"></a>Получение наилучшей производительности

Некоторые конфигурации оборудования могут вызвать проблемы с производительностью в Windows Mixed Reality. Для таких проблем, как низкая загрузка, прерывистый визуальный элемент или плохое качество визуального элемента, попробуйте следующие общие исправления:

* Закройте все открытые приложения, работающие на рабочем столе компьютера.
* Если вы используете адаптер HDMI USB-C или Дисплайпорт, попробуйте другой. См. Рекомендуемые адаптеры
* Если к графической плате компьютера подключены дополнительные мониторы, отключите их.
* Попробуйте скачать некоторые различные приложения смешанной реальности из Магазина Windows. Некоторые из них могут работать лучше с установкой компьютера.

> [!NOTE]
> Если появится сообщение "Эта конфигурация оборудования может работать с Windows Mixed Reality, но еще не тестировалась", при запуске Windows Mixed Reality для длительных сеансов может возникнуть ряд проблем с производительностью.

## <a name="see-also"></a>См. также статью

* [Спросить у сообщества](https://answers.microsoft.com)
* [Свяжитесь с нами для получения поддержки](https://support.microsoft.com/contactus/)
* [Устранение неполадок](troubleshooting-windows-mixed-reality.md)