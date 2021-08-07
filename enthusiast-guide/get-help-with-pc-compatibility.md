---
title: Получение справки по совместимости ПК
description: используйте ресурсы для решения проблем совместимости пк при работе с Windows Mixed Reality приложениями и устройствами.
author: hferrone
ms.author: v-hferrone
ms.date: 01/07/2021
ms.topic: article
keywords: Windows Mixed Reality, смешанная реальность, виртуальная реальность, VR, MR, обратная связь, центр обратной связи, ошибки
appliesto:
- Windows 10
ms.openlocfilehash: cd5598147823670d1aa00eddda844bea21d7da262339624613f3724cbc5157fa
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189216"
---
# <a name="get-help-with-pc-compatibility-in-windows-mixed-reality"></a>Получение справки по совместимости ПК в Windows Mixed Reality

при настройке Windows Mixed Reality или с помощью [портала смешанной реальности](install-windows-mixed-reality.md)вы получите отчет о том, работает ли ваш компьютер с задачей. Мы разработали определенные сведения о том, что можно увидеть в следующих разделах.

Прежде чем продолжить, попробуйте использовать наиболее распространенные исправления ниже. 

> [!div class="checklist"]
> * Убедитесь, что компьютер соответствует [минимальным требованиям к совместимости оборудования ПК](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
> * Проверьте совместимость [графического адаптера и процессора](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)
> * Проверьте список [рекомендуемых адаптеров](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
> * обновите графический драйвер, выбрав **пуск > Параметры > обновление & безопасность > проверить наличие обновлений** 

Если вы хотите получить контакт, [обратитесь в](https://answers.microsoft.com) [службу поддержки](https://support.microsoft.com/contactus/)или воспользуйтесь сведениями об [устранении неполадок](troubleshooting-windows-mixed-reality.md) .

## <a name="youre-good-to-go"></a>Все готово

Хорошая новость. Если вы видите сообщение " **вы действительно хотите пройти?** ", ваш компьютер может работать Windows Mixed Reality! По-прежнему существуют различия между оборудованием и конфигурацией компьютера, поэтому возможности смешанной реальности могут отличаться на разных ПК.

## <a name="supports-some-features"></a>Поддерживает некоторые функции

если вы видите сообщение о том, что **компонент поддерживает некоторые функции** , ваш компьютер может запускать некоторые Windows Mixed Realityные возможности, но не может предоставить лучшие возможности. К возможным недостаткам относятся задержкой графика, попадания в производительность, а также некоторые приложения и игры, которые не могут быть запущены. Мы добавили сообщения, которые вы можете увидеть, и о том, что делать с ними:

* [На этом компьютере имеется Интегрированная графическая карта с одним каналом ОЗУ](#this-pc-has-an-integrated-graphics-card-with-single-channel-ram)
* [На этом компьютере имеется Конфигурация гибридной графики с несовместимой связью PCIe](#this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link)
* [Графический драйвер этого компьютера может плохо работать с Windows Mixed Reality](#this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality)
* [Процессор этого компьютера может не работать с Windows Mixed Reality](#this-pcs-processor-might-not-work-well-with-windows-mixed-reality)
* [У этого компьютера может не быть совместимой конфигурации USB](#this-pc-might-not-have-a-compatible-usb-configuration)
* [на этом компьютере нет Bluetooth 4,0 для контроллеров](#this-pc-doesnt-have-bluetooth-40-for-controllers)
* [в зависимости от гарнитуры может потребоваться Bluetooth адаптер для использования контроллеров движения.](#depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers)
* [На этом компьютере нет USB-порта с самостоятельным питанием](#this-pc-doesnt-have-a-self-powered-usb-port)
* [Графическая карта этого компьютера не будет работать с Windows Mixed Reality](#this-pcs-graphics-card-wont-work-with-windows-mixed-reality)
* [Графический драйвер этого компьютера не будет работать с Windows Mixed Reality](#this-pcs-graphics-driver-wont-work-with-windows-mixed-reality)
* [Процессор этого ПК не будет работать с Windows Mixed Reality](#this-pcs-processor-wont-work-with-windows-mixed-reality)
* [На этом компьютере недостаточно свободного дискового пространства для запуска Windows Mixed Reality](#this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality)
* [на этом компьютере работает выпуск Windows, который не поддерживает Windows Mixed Reality](#this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality)
* [На этом компьютере не установлена последняя версия Windows 10](#this-pc-isnt-running-the-latest-version-of-windows-10)
* [Этот компьютер не имеет порта USB 3,0](#this-pc-has-no-usb-30-port)
* [Невозможно запустить это приложение через удаленный рабочий стол](#you-cant-run-this-app-via-remote-desktop)

### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>На этом компьютере имеется Интегрированная графическая карта с одним каналом ОЗУ

интегрированные графические карты обеспечивают лучшие Windows Mixed Reality на компьютерах с двухканальной памятью. При возникновении проблем с производительностью выполните следующие действия.

> [!div class="checklist"]
> * Установка [совместимой дискретной графической карты](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)
> * Установка дополнительного ОЗУ для создания двухканальной памяти
> * Переключиться на [совместимый компьютер](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>На этом компьютере имеется Конфигурация гибридной графики с несовместимой связью PCIe

PCIe означает подключение *периферийных компонентов*, которое используется компьютером для связи с графической картой. Конфигурация может работать, но при возникновении проблем необходимо переключиться на [совместимый компьютер](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>Графический драйвер этого компьютера может плохо работать с Windows Mixed Reality

попробуйте скачать новый графический драйвер с помощью Центр обновления Windows, выполнив следующие действия.

> [!div class="checklist"]
> * выберите **пуск > Параметры > обновление & безопасность > проверить наличие обновлений** или перейти на веб-сайт изготовителя пк или графической платы
> * [Проверка обновлений](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Если это не сработает, вам потребуется:

> [!div class="checklist"]
> * Добавление [совместимой графической карты](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Переключиться на [совместимый компьютер](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>Процессор этого компьютера может не работать с Windows Mixed Reality

процессор компьютера может плохо работать с Windows Mixed Reality, так как на нем недостаточно ядер. если Windows Mixed Reality не работает правильно:

> [!div class="checklist"]
> * Замените процессор [совместимым одним](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) 
> * Переключиться на [совместимый компьютер](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>У этого компьютера может не быть совместимой конфигурации USB

Для проблем, связанных с Windows Mixed Reality:

> [!div class="checklist"]
> * Рекомендации по распространенным проблемам совместимости см. в [документации по рекомендуемым адаптерам](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) .
> * Рассмотрите возможность использования [внешнего электропитания USB-концентратора](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets)

Если проблемы не удается устранить:

> [!div class="checklist"]
> * Подключите гарнитуру к другому USB-порту, если он доступен.
> * Если это не поможет, удалите текущий USB-драйвер компьютера, а затем переустановите драйвер Microsoft:

1. Нажмите кнопку **Пуск** и в поле **поиска** введите "Диспетчер устройств".
2. Выберите **Диспетчер устройств** из результатов.
3. Разверните категорию для контроллеров универсальной последовательной шины, просмотрите список устройств и удалите несовместимые драйверы.
    * Если список содержит элемент "расширяемый контроллер узла", который не содержит "Microsoft" в конце имени устройства, этот драйвер несовместим с Windows Mixed Reality. Его необходимо удалить. Чтобы удалить драйвер, щелкните правой кнопкой мыши устройство в списке и выберите **удалить устройство**. Установите флажок **удалить программное обеспечение драйвера для этого устройства** , а затем выберите **Удалить**.
    * Если список содержит элемент "расширяемый контроллер узла", включающий в себя "Етрон", этот USB-контроллер не совместим с Windows Mixed Reality. Вам потребуется использовать другой USB-порт на компьютере или приобрести другой USB-контроллер узла 3,0.
4. Перезагрузите компьютер.
5. Вернитесь к диспетчер устройств и еще раз нахождение расширяемого элемента контроллера узла. Если теперь в конце имени устройства отображается «Microsoft», то все готово. В противном случае повторите действия по удалению, чтобы удалить все дополнительные версии драйвера, отличные от Майкрософт.

> [!div class="checklist"]
> * Если это не поможет, добавьте USB-карту PCIe на компьютер.

### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>на этом компьютере нет Bluetooth 4,0 для контроллеров

2018 и более новые Windows Mixed Reality гарнитуры уже имеют встроенные Bluetooth, но если у вас старая гарнитура, для контроллеров движения смешанной реальности требуется Bluetooth 4,0. вы по-прежнему можете [использовать Windows Mixed Reality с контроллером Xbox](motion-controller-problems.md#can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset), [мышью, клавиатурой](/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home#keyboard-and-mouse)или [USB-адаптером Bluetooth для подключения контроллеров движения](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology) к компьютеру. [См. Рекомендуемые адаптеры](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers"></a>в зависимости от гарнитуры может потребоваться Bluetooth адаптер для использования контроллеров движения.

некоторые гарнитуры имеют Bluetooth встроенные, поэтому контроллеры могут напрямую связываться с наушниками. для использования контроллеров движения другие необходимы Bluetooth радио на компьютере (или отдельный аппаратный ключ). Дополнительные сведения см. на странице [рекомендуемых адаптеров](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#windows-mixed-reality-compatible-usb-bluetooth-adapters) .

### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>На этом компьютере нет USB-порта с самостоятельным питанием

порт USB 3,0 с самостоятельным питанием необходим для подключения гарнитуры Windows Mixed Reality. Подключение на пк [подключенный USB-концентратор 3,0](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets) и использовать его для подключения гарнитуры.

### <a name="this-pcs-graphics-card-wont-work-with-windows-mixed-reality"></a>Графическая карта этого компьютера не будет работать с Windows Mixed Reality

Графическая плата этого компьютера несовместима с Windows Mixed Reality. Вам потребуется выполнить указанные ниже действия:

> [!div class="checklist"]
> * Добавление [совместимой графической карты](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Переключиться на [совместимый компьютер](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-graphics-driver-wont-work-with-windows-mixed-reality"></a>Графический драйвер этого компьютера не будет работать с Windows Mixed Reality

Графический драйвер этого компьютера не будет работать с Windows Mixed Reality. попробуйте скачать новый графический драйвер с помощью Центр обновления Windows, выполнив следующие действия.

> [!div class="checklist"]
> * выберите **пуск > Параметры > обновление & безопасность > проверить наличие обновлений** или перейти на веб-сайт изготовителя пк или графической платы
> * [Проверка обновлений](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Если это не сработает, вам потребуется:

> [!div class="checklist"]
> * Добавление [совместимой графической карты](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Переключиться на [совместимый компьютер](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-processor-wont-work-with-windows-mixed-reality"></a>Процессор этого ПК не будет работать с Windows Mixed Reality

Процессор этого компьютера не поддерживает инструкции AVX/Попкнт. для запуска Windows Mixed Reality необходимо следующее:

> [!div class="checklist"]
> * Заменить его на [совместимую графическую карту](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Переключиться на [совместимый компьютер](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality"></a>На этом компьютере недостаточно свободного дискового пространства для запуска Windows Mixed Reality

Windows Mixed Reality требуется 10 гб свободного дискового пространства для установки и лучшей производительности. Освободите место на диске и повторите настройку с самого начала.

### <a name="this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality"></a>на этом компьютере работает выпуск Windows, который не поддерживает Windows Mixed Reality

Windows Mixed Reality работает в [Windows 10 Домашняя](https://www.microsoft.com/p/windows-10-home/d76qx4bznwk4?activetab=pivot:overviewtab) и [Windows 10 Pro](https://www.microsoft.com/p/windows-10-pro/DF77X4D43RKT?icid=W10Pro_upsell_071817&activetab=pivot:overviewtab). Для использования Windows Mixed Reality необходимо установить один из этих выпусков.

### <a name="this-pc-isnt-running-the-latest-version-of-windows-10"></a>На этом компьютере не установлена последняя версия Windows 10

для Windows Mixed Reality требуется Windows 10 Fall Creators Update. [Обновите свой ПК](https://support.microsoft.com/help/4028685) и повторите попытку.

### <a name="this-pc-has-no-usb-30-port"></a>Этот компьютер не имеет порта USB 3,0

для подключения гарнитуры Windows Mixed Reality вам потребуется порт USB 3,0. Если вы используете настольный ПК, добавьте USB-карту PCIe. Для ноутбуков необходимо переключиться на [совместимый компьютер](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="you-cant-run-this-app-via-remote-desktop"></a>Невозможно запустить это приложение через удаленный рабочий стол

чтобы использовать Windows Mixed Reality, необходим пк с подключенным монитором. Если вы используете виртуальную машину или не используете монитор, попробуйте использовать виртуальный адаптер отображения. Это устройство, которое подключается к Дисплайпорту ПК и эмулирует экран компьютера.

## <a name="getting-the-best-performance"></a>Получение наилучшей производительности

Некоторые конфигурации оборудования могут вызвать проблемы с производительностью Windows Mixed Reality. Для таких проблем, как низкая загрузка, прерывистый визуальный элемент или плохое качество визуального элемента, попробуйте следующие общие исправления:

* Закройте все открытые приложения, работающие на рабочем столе компьютера
* Если вы используете адаптер HDMI USB-C или Дисплайпорт, попробуйте другой. См. Рекомендуемые адаптеры
* При наличии дополнительных мониторов, подключенных к графической плате компьютера, отключите их.
* попробуйте скачать некоторые различные приложения смешанной реальности из хранилища Windows. некоторые могут работать лучше с программой установки компьютера
* Ознакомьтесь с [документацией по вопросам производительности](performance-questions.md)

если у вас по-прежнему возникают проблемы с производительностью, обновите следующие параметры [Windows Mixed Reality](set-up-windows-mixed-reality.md) для оптимального взаимодействия с пользователем:

* Взаимодействие
* Решение
* Частота кадров
* Калибровка

> [!NOTE]
> если появится сообщение «эта конфигурация оборудования может работать с Windows Mixed Reality, но еще не тестировалась», при выполнении Windows Mixed Reality для длинных сеансов можно столкнуться с некоторыми проблемами производительности.

## <a name="working-with-steamvr"></a>Работа с Стеамвр

Замечательные игры от Стеамвр — это отличный способ испытать все, что требуется для работы с VR. Тем не менее, необходимо убедиться, что вы [получаете максимальную производительность](performance-questions.md) для вашего иммерсивного устройства. После установки [Steam](https://store.steampowered.com/about)выполните следующие действия.

* Следуйте инструкциям по [использованию стеамвр с Windows Mixed Reality](using-steamvr-with-windows-mixed-reality.md)
* Установка приложений для [тестирования производительности стеамвр](https://store.steampowered.com/app/323910/SteamVR_Performance_Test)

## <a name="next-vr-checkpoint"></a>Следующая контрольная точка VR

Если вы выполняете описанные выше пути к VR, вы почти готовы купить устройство. Отсюда вы можете перейти к последней до приобретения контрольной точки:

> [!div class="nextstepaction"]
> [Приобретение часто задаваемых вопросов](before-you-buy-faqs.md)

Или перейдите сразу к разделу Приступая к работе:

> [!div class="nextstepaction"]
> [Настройка Windows Mixed Reality](set-up-windows-mixed-reality.md)

Вы всегда можете вернуться к [пути VR](vr-journey.md) в любое время.