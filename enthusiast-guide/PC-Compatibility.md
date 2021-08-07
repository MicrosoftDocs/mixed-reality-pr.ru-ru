---
title: Windows Mixed Reality Приложение проверки компьютеров
description: как найти и использовать приложение Windows Mixed Reality PC Check для проверки совместимости компьютера перед покупкой головной гарнитуры Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, смешанная реальность, виртуальная реальность, VR, MR, совместимый, совместимость, пк, требования к системе
appliesto:
- Windows 10
ms.openlocfilehash: 463e7dfc2c95ed9efc70a87ebbb0dac08b134251401a1114f3b9a364aa197073
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188052"
---
# <a name="windows-mixed-reality-pc-check-app"></a>Windows Mixed Reality Приложение проверки компьютеров

приложение **[Windows Mixed Reality pc Check](https://www.microsoft.com/store/p/windows-mixed-reality-pc-check/9nzvl19n7cnc)** — это лучший способ убедиться, что компьютер готов к запуску Windows Mixed Reality. приложение Windows Mixed Reality PC Check работает только на компьютерах с установленным по крайней мере Windows 10 версией 1607. чтобы проверить версию Windows, введите "winver" в строке поиска и выполните команду. для Windows 10 версий, предшествующих 1607, приложение по-прежнему будет отображаться в хранилище, но при попытке установки вы получите сообщение об ошибке.

<a href="https://www.microsoft.com/store/productid/9NZVL19N7CNC"><img alt="Download Windows Mixed Reality PC Check app" src="images/WMR-PC-Check-app.png"/></a>

После запуска приложения вы получите одно из следующих сообщений:

* **Все готово.** Ваш ПК требует выполнения Windows Mixed Reality.
* **Вы почти находитесь.** этот компьютер может работать Windows Mixed Reality, но некоторые функции могут быть ограничены.
* **Не удается запустить смешанную реальность.** Этот компьютер не соответствует минимальным требованиям, необходимым для запуска Windows Mixed Reality.

Затем вы получите анализ вашего компьютера в соответствии с требуемым оборудованием, драйверами и операционной системой.
![снимок экрана: проверка Windows Mixed Reality пк](images/screenshot-mr-pc-check.jpg) 

<table>
<tr>
<th>Значок</th><th>Что это означает</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">Ваш компьютер передает требуемый элемент.</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">Возможны проблемы с вашим компьютером для данного требования. При возникновении проблем может потребоваться устранение неполадок или обновление компьютера.</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">Ваш компьютер не соответствует требованиям для указанного элемента.</td>
</tr>
</table>

## <a name="get-help-with-windows-mixed-reality-pc-check-results"></a>получение справки по Windows Mixed Reality результатам проверки компьютера

при настройке Windows Mixed Reality или запуске Windows Mixed Realityного приложения проверки компьютера на компьютере вы получите отчет о совместимости. Ниже приведены некоторые сведения о том, что можно увидеть.

### <a name="youre-good-to-go"></a>![Все готово](images/glyph-succeeded.png)

Хорошие новости — ваш компьютер может работать Windows Mixed Reality. Следует помнить, что между оборудованием и настройкой компьютера по-прежнему существуют различия. Возможности смешанной реальности могут отличаться на разных ПК.

>[!NOTE]
>если появится сообщение «эта конфигурация оборудования может работать с Windows Mixed Reality, но еще не тестировалась», при выполнении Windows Mixed Reality для длинных сеансов можно столкнуться с некоторыми проблемами производительности.

### <a name="youre-nearly-there"></a>![Вы почти находитесь](images/glyph-warning.png)

ваш компьютер должен иметь возможность запускать Windows Mixed Reality, но может не обеспечивать наилучшее удобство работы. Графика может отставать, некоторые приложения и игры могут работать неправильно, и некоторые могут вообще не работать.

Ниже приведены сообщения, которые вы можете увидеть, и что делать с ними:

#### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>На этом компьютере имеется Интегрированная графическая карта с одним каналом ОЗУ

интегрированные графические карты обеспечивают лучшие Windows Mixed Reality на компьютерах с двухканальной памятью. При возникновении проблем с производительностью выполните следующие действия.

* Установите [совместимую дискретную графическую карту](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).
* Установите дополнительный ОЗУ, чтобы создать двухканальный ОЗУ.
* Переключитесь на [совместимый компьютер](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>На этом компьютере имеется Конфигурация гибридной графики с несовместимой связью PCIe

PCIe означает, что *устройство Interconnect для периферийных компонентов Express*. Это подключение, используемое ПК для связи с графической картой. Конфигурация может работать, но при возникновении проблем необходимо переключиться на [совместимый компьютер](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>Графический драйвер этого компьютера может плохо работать с Windows Mixed Reality

если возникли проблемы, попробуйте загрузить новый графический драйвер с помощью Центр обновления Windows (**Start > Параметры > обновление & безопасность > проверить наличие обновлений**) — или обратитесь к изготовителю пк или к веб-сайту производителя видеоплаты.

Если это не сработает, необходимо добавить [совместимую графическую карту](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) или переключиться на [совместимый компьютер](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>Процессор этого компьютера может не работать с Windows Mixed Reality

процессор этого пк может не работать с Windows Mixed Reality, так как у него недостаточно ядер. если Windows Mixed Reality работает неправильно, обновите его до [совместимого](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) компьютера или переключитесь на [совместимый компьютер](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>У этого компьютера может не быть совместимой конфигурации USB

При возникновении проблем с Windows Mixed Reality:

* Подключите гарнитуру к другому USB-порту, если он доступен.
* Если это не поможет, удалите текущий USB-драйвер компьютера, а затем переустановите драйвер Microsoft:

1. Нажмите кнопку **Пуск** и в поле поиска введите **"Диспетчер устройств"** .
1. Выберите **Диспетчер устройств** из результатов.
1. Разверните категорию для контроллеров универсальной последовательной шины, просмотрите список устройств и удалите несовместимые драйверы. 
 * Если список содержит элемент "расширяемый контроллер узла" без "Microsoft" в конце имени устройства, драйвер не совместим с Windows Mixed Reality. Его необходимо удалить. Чтобы удалить драйвер, щелкните правой кнопкой мыши устройство в списке и выберите **удалить устройство**. Установите флажок **удалить программное обеспечение драйвера для этого устройства** , а затем выберите **Удалить**.
 * Если список содержит элемент "расширяемый контроллер узла", включающий в себя "Етрон", этот USB-контроллер не совместим с Windows Mixed Reality. Вам потребуется использовать другой USB-порт на компьютере или приобрести другой USB-контроллер узла 3,0.
1. Перезагрузите компьютер. 
1. Вернитесь к диспетчер устройств и еще раз нахождение расширяемого элемента контроллера узла. Если теперь в конце имени устройства отображается «Microsoft», то все готово. В противном случае повторите действия по удалению, чтобы удалить все дополнительные версии драйвера, не относящиеся к корпорации Майкрософт.
* Если это не поможет, добавьте USB-карту PCIe на компьютер.

#### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>на этом компьютере нет Bluetooth 4,0 для контроллеров.

#### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>На этом компьютере нет USB-порта с самостоятельным питанием.

#### <a name="this-pc-should-work-but-youll-have-the-best-experience-with-a-high-performance-intel-processor"></a>Этот компьютер должен работать, но у вас будет оптимальный опыт работы с высокопроизводительным процессором Intel®.

### <a name="cant-run-mixed-reality"></a>![Не удается запустить смешанную реальность](images/glyph-error.png)

 [получение справки по Windows Mixed Reality результатам проверки компьютера](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)
