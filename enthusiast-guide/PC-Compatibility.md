---
title: Приложение для проверки компьютеров Windows Mixed Reality
description: Как найти и использовать приложение "Проверка компьютеров Windows Mixed Reality" для проверки совместимости компьютера перед покупкой гарнитуры Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, Смешанная реальность, виртуальная реальность, VR, MR, совместимый, совместимость, ПК, требования к системе
appliesto:
- Windows 10
ms.openlocfilehash: 6dc187b14950f1446fd5e60c3e6db10fd2c3ce25
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725435"
---
# <a name="windows-mixed-reality-pc-check-app"></a>Приложение для проверки компьютеров Windows Mixed Reality

Приложение " **[Проверка компьютеров Windows Mixed Reality](https://www.microsoft.com/store/p/windows-mixed-reality-pc-check/9nzvl19n7cnc)** " — это лучший способ убедиться, что компьютер готов к запуску Windows Mixed Reality. Приложение для проверки компьютеров Windows Mixed Reality работает только на компьютерах с установленной версией Windows 10 1607. Чтобы проверить версию Windows, введите "winver" в строке поиска и выполните команду. Для версий Windows 10, более ранних, чем 1607, приложение по-прежнему будет отображаться в хранилище, но при попытке установки вы получите сообщение об ошибке.

<a href="https://www.microsoft.com/store/productid/9NZVL19N7CNC"><img alt="Download Windows Mixed Reality PC Check app" src="images/WMR-PC-Check-app.png"/></a>

После запуска приложения вы получите одно из следующих сообщений:

* **Все готово.** Ваш ПК занимается выполнением Windows Mixed Reality.
* **Вы почти находитесь.** Этот компьютер может работать под управлением Windows Mixed Reality, но некоторые функции могут быть ограничены.
* **Не удается запустить смешанную реальность.** Этот компьютер не соответствует минимальным требованиям, необходимым для запуска Windows Mixed Reality.

Затем вы получите анализ вашего компьютера в соответствии с требуемым оборудованием, драйверами и операционной системой.
![Снимок экрана: проверка компьютера Windows Mixed Reality](images/screenshot-mr-pc-check.jpg) 

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

## <a name="get-help-with-windows-mixed-reality-pc-check-results"></a>Получение справки по результатам проверки компьютеров Windows Mixed Reality

При настройке Windows Mixed Reality или запуске приложения для проверки компьютеров Windows Mixed Reality на компьютере вы получите отчет о совместимости. Ниже приведены некоторые сведения о том, что можно увидеть.

### <a name="youre-good-to-go"></a>![Все готово](images/glyph-succeeded.png)

Хорошие новости — ваш компьютер может работать под управлением Windows Mixed Reality. Следует помнить, что между оборудованием и настройкой компьютера по-прежнему существуют различия. Возможности смешанной реальности могут отличаться на разных ПК.

>[!NOTE]
>Если появится сообщение "Эта конфигурация оборудования может работать с Windows Mixed Reality, но еще не тестировалась", при запуске Windows Mixed Reality для длительных сеансов может возникнуть ряд проблем с производительностью.

### <a name="youre-nearly-there"></a>![Вы почти находитесь](images/glyph-warning.png)

Ваш компьютер должен иметь возможность работать под управлением Windows Mixed Reality, но может не обеспечивать наилучших возможностей. Графика может отставать, некоторые приложения и игры могут работать неправильно, и некоторые могут вообще не работать.

Ниже приведены сообщения, которые вы можете увидеть, и что делать с ними:

#### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>На этом компьютере имеется Интегрированная графическая карта с одним каналом ОЗУ

Интегрированные графические карты предоставляют лучшие возможности Windows Mixed Reality на компьютерах с двухканальной ПАМЯТЬю. При возникновении проблем с производительностью выполните следующие действия.

* Установите [совместимую дискретную графическую карту](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).
* Установите дополнительный ОЗУ, чтобы создать двухканальный ОЗУ.
* Переключитесь на [совместимый компьютер](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>На этом компьютере имеется Конфигурация гибридной графики с несовместимой связью PCIe

PCIe означает, что *устройство Interconnect для периферийных компонентов Express*. Это подключение, используемое ПК для связи с графической картой. Конфигурация может работать, но при возникновении проблем необходимо переключиться на [совместимый компьютер](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>Графический драйвер этого компьютера может не работать с Windows Mixed Reality

Если возникли проблемы, попробуйте скачать новый графический драйвер с помощью Центр обновления Windows (**Параметры запуска > > обновить & безопасность > проверить наличие обновлений**) — или обратитесь к изготовителю ПК или к веб-сайту производителя видеоплаты.

Если это не сработает, необходимо добавить [совместимую графическую карту](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) или переключиться на [совместимый компьютер](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>Процессор этого компьютера может не работать с Windows Mixed Reality

Процессор этого компьютера может не работать с Windows Mixed Reality, так как у него недостаточно ядер. Если Windows Mixed Reality работает неправильно, обновите ее до [совместимого](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) компьютера или переключитесь на [совместимый компьютер](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>У этого компьютера может не быть совместимой конфигурации USB

Если возникли проблемы с Windows Mixed Reality, выполните следующие действия.

* Подключите гарнитуру к другому USB-порту, если он доступен.
* Если это не поможет, удалите текущий USB-драйвер компьютера, а затем переустановите драйвер Microsoft:

1. Нажмите кнопку **Пуск** и в поле поиска введите **"Диспетчер устройств"** .
1. Выберите **Device Manager** из результатов.
1. Разверните категорию для контроллеров универсальной последовательной шины, просмотрите список устройств и удалите несовместимые драйверы. 
 * Если список содержит элемент "расширяемый контроллер узла" без "Microsoft" в конце имени устройства, драйвер не совместим с Windows Mixed Reality. Его необходимо удалить. Чтобы удалить драйвер, щелкните правой кнопкой мыши устройство в списке и выберите **удалить устройство**. Установите флажок **удалить программное обеспечение драйвера для этого устройства** , а затем выберите **Удалить**.
 * Если список содержит элемент "расширяемый контроллер узла", включающий в себя "Етрон", этот USB-контроллер не совместим с Windows Mixed Reality. Вам потребуется использовать другой USB-порт на компьютере или приобрести другой USB-контроллер узла 3,0.
1. Перезагрузите компьютер. 
1. Вернитесь к Device Manager и еще раз нахождение расширяемого элемента контроллера узла. Если теперь в конце имени устройства отображается «Microsoft», то все готово. В противном случае повторите действия по удалению, чтобы удалить все дополнительные версии драйвера, не относящиеся к корпорации Майкрософт.
* Если это не поможет, добавьте USB-карту PCIe на компьютер.

#### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>На этом компьютере нет Bluetooth 4,0 для контроллеров.

#### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>На этом компьютере нет USB-порта с самостоятельным питанием.

#### <a name="this-pc-should-work-but-youll-have-the-best-experience-with-a-high-performance-intel-processor"></a>Этот компьютер должен работать, но у вас будет оптимальный опыт работы с высокопроизводительным процессором Intel®.

### <a name="cant-run-mixed-reality"></a>![Не удается запустить смешанную реальность](images/glyph-error.png)

 [Получение справки по результатам проверки компьютеров Windows Mixed Reality](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)
