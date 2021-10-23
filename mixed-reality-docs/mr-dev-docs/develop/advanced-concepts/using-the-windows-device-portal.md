---
title: Использование портала устройств Windows
description: Сведения о том, как настраивать устройства удаленно через Wi-Fi или USB с помощью портала устройств Windows, а также как управлять ими.
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: Портал устройств Windows, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 2cdc0733a836fe3673be0ea065898e282419970e
ms.sourcegitcommit: bea83261bf9ce7a27a618e5bc54dc4d7711f5435
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2021
ms.locfileid: "130159110"
---
# <a name="using-the-windows-device-portal"></a>Использование портала устройств Windows

| Функция          | [HoloLens (1-го поколения)](/hololens/hololens1-hardware) | [HoloLens 2](/hololens/hardware) | 
|:------------:|:--------------------------------------------------------------------------:|:---------------------------------------------------------:|
| Портал устройств Windows | :heavy_check_mark:               | :heavy_check_mark: |

Портал устройств Windows для HoloLens позволяет настроить устройство и управлять им удаленно по подключению через Wi-Fi или USB. Портал устройств — это веб-сервер на вашем устройстве HoloLens, к которому можно подключаться из веб-браузера на ПК. Портал устройств содержит множество инструментов, которые помогут вам управлять HoloLens, отлаживать и оптимизировать приложения.

Эта документация посвящена исключительно порталу устройств Windows для HoloLens. Чтобы использовать портал устройств Windows для ПК (в том числе для Windows Mixed Reality), изучите [этот обзор](/windows/uwp/debug-test-perf/device-portal).

> [!NOTE]
> Портал устройств — это средство разработчика, которое не предназначено для использования в приложениях, развернутых в организации.

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>Настройка HoloLens для использования портала устройств Windows

1. Включите устройство HoloLens и наденьте его.
2. Выполните [жест "Пуск"](/hololens/hololens2-basic-usage#start-gesture) для HoloLens2 или [жест "раскрытая ладонь"](/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom) для HoloLens (1-го поколения), чтобы открыть главное меню. 
3. Посмотрите на плитку **Settings** (Параметры) и выполните [жест касания](/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap) в HoloLens (1-го поколения). Для выбора элемента в HoloLens 2 можно [коснуться его или использовать телекинез](/hololens/hololens2-basic-usage). 
4. Выберите пункт меню **Обновить**.
5. Выберите пункт меню **Для разработчиков**.
6. Включите **Режим разработчика**.

> [!IMPORTANT]
> Если вы выполнили вход в многопользовательском режиме, а не с правами администратора, возможность использования режима разработчика может быть недоступна. Убедитесь, что вы являетесь **[администратором на устройстве](/hololens/security-adminless-os)** .

7. [Прокрутите вниз](../../design/gaze-and-commit.md#composite-gestures) и включите **Портал устройств**.
8. Если вы настраиваете портал устройств Windows для развертывания приложений на этом устройстве HoloLens через подключение USB или Wi-Fi, щелкните **Pair** (Связать) для [создания ПИН-кода связывания](using-visual-studio.md). Оставьте приложение "Параметры" и окно PIN-кода открытым, пока не закончите ввод PIN-кода в Visual Studio в процессе первого развертывания.

![Включение режима разработчика в приложении "Параметры" для Windows Holographic](images/using-windows-portal-img-01.jpg)

## <a name="connecting-over-wi-fi"></a>Подключение через Wi-Fi

1. [Подключите устройство HoloLens к Wi-Fi](/hololens/hololens-network).
2. Найдите IP-адрес устройства одним из следующих способов:
  * Выберите последовательно **Settings > Network & Internet > Wi-Fi > Advanced Options** (Параметры > Сеть и Интернет > Wi-Fi > Расширенные параметры).
  * Выберите **Settings > Network & Internet** (Параметры > Сеть и Интернет) и **Свойства оборудования**.
  * Использование голосовой команды "What's my IP address?"

![Параметры HoloLens 2](images/using-windows-portal-img-02.jpg)

3. В веб-браузере на компьютере откройте страницу https://<IP-адрес вашего устройства HOLOLENS>.
   * В браузере отобразится следующее сообщение: "There's a problem with this website's security certificate" (Возникла проблема с сертификатом безопасности этого сайта), так как для нашего портала устройств выдан тестовый сертификат. Вы можете игнорировать эту ошибку сертификата и продолжить работу.

## <a name="connecting-over-usb"></a>Подключение через USB

> [!IMPORTANT]
> IpOverUsb больше не рекомендуется использовать для новых стандартов браузера, так как для этого требуется порт 10080. Если вы по-прежнему хотите использовать IpOverUsb, установите флажок USB Device Connectivity (Подключение USB-устройства) во время установки Visual Studio, который не установлен по умолчанию. Вместо этого мы рекомендуем подключаться с помощью UsbNcm, который поддерживается на HoloLens 2 по умолчанию. Если вы используете HoloLens 1, рекомендуем подключиться к компьютеру с помощью Wi-Fi.

1. Если на HoloLens 2 установлена Windows Holographic 21H1 или более поздней версии, перейдите в раздел For developers (Для разработчиков) в приложении Settings (Параметры) и включите обнаружение устройств. 
2. Подключите HoloLens 2 к ПК с помощью кабеля USB-C.
3. Найдите IP-адрес UsbNcm. Это можно сделать несколькими способами.
  * В приложении Settings (Параметры) на устройстве (этот метод работает только для HoloLenses с Windows Holographic 21H1 или более поздней версии с включенным обнаружением устройств)
    1. Перейдите в приложение Settings (Параметры) на устройстве.
    2. Последовательно выберите элементы Update & Security > For developers (Обновление и безопасность > Для разработчиков). Здесь же вы включали портал устройств.
    3. В нижней части страницы скопируйте IP-адрес **Ethernet**. Это ваш IP-адрес UsbNcm. 
    ![Параметры HoloLens 2 — IP-адрес UsbNcm](images/deviceportal_usbncm_ipaddress.jpg)

  * На портале устройств 
    1. На устройстве откройте портал устройств, используя адрес Wi-Fi HoloLens. Если вы не знаете адрес Wi-Fi HoloLens, можно использовать голосовую команду "What's my IP address".
    2. Перейдите в раздел System > Networking (Система > Сеть)
    3. В правой части страницы на панели IP Configuration (IP-конфигурация) выберите раздел, начинающийся с Description: UsbNcm Function (Описание: функция UsbNcm).
    4. IP-адрес UsbNcm указан в строке IPv4 address. Вы можете скопировать или просто щелкнуть адрес — это гиперссылка, которая будет повторно открывать портал устройств с помощью IP-адреса UsbNcm.
  
  * В командной строке
    1. В любой командной строке перейдите в папку bin\<SDK version>\x86, где установлен пакет SDK для Windows 10, например C:\Program Files (x86)\Windows Kits\10\bin\10.0.19041.0\x86.
    2. Введите "winappdeploycmd devices" и нажмите клавишу ВВОД.
    3. В выходных данных найдите запись, в которой столбец Model/Name содержит имя вашего устройства HoloLens, например HOLOLENS-xxxxxx. IP-адрес UsbNcm находится в начале этой строки и будет автоматическим частным IP-адресом в формате 169.254.x.x. Скопируйте этот адрес. 
 
4. Если вы скопировали IP-адрес UsbNcm, в веб-браузере на своем ПК перейдите по адресу: https:// + ваш IP-адрес UsbNcm.

### <a name="moving-files-over-usb"></a>Перемещение файлов по USB

Вы можете перемещать файлы с компьютера на HoloLens без дополнительных настроек.
1. Подключите компьютер к HoloLens с помощью USB-кабеля.
2. Перетащите файлы в папку **Этот компьютер\\[имя_вашего_устройства_HoloLens]\Internal Storage** на рабочем столе.
3. Откройте меню **Пуск** и выберите **Все программы > Проводник** в HoloLens.

> [!NOTE]
> Вам может потребоваться выбрать **Это устройство** в области слева, чтобы выйти из меню "Последние" и найти свои файлы. 

## <a name="connecting-to-an-emulator"></a>Подключение к эмулятору

Можно также использовать Портал устройства вместе с эмулятором. Чтобы подключиться к порталу устройств, воспользуйтесь [панелью инструментов](using-the-hololens-emulator.md). Выберите этот значок: ![Значок открытия портала устройств](images/emulator-deviceportal.png) **Открыть портал устройств**. Открывает в эмуляторе портал устройств Windows для HoloLens OS.

## <a name="creating-a-username-and-password"></a>Создание имени пользователя и пароля

![Настройка доступа к порталу устройств Windows](images/windows-device-portal-credentials-reset-page-1000px.png)<br>
*Настройка доступа к порталу устройств Windows*

При первом подключении к порталу устройств на устройстве HoloLens нужно будет создать имя пользователя и пароль.
1. В веб-браузере на компьютере введите IP-адрес HoloLens. Откроется страница Setup access (Настройка доступа).
2. Выберите элемент **Request pin** (Запросить ПИН-код) и посмотрите на дисплей HoloLens, чтобы получить созданный ПИН-код.
3. Введите PIN-код в поле **PIN displayed on your device** (PIN-код, который отображается на устройстве).
4. Введите имя пользователя, которое будет использоваться для подключения к порталу устройств. Это не должно быть именем учетной записи Майкрософт (MSA) или доменным именем.
5. Введите пароль и подтвердите его. Длина пароля не должна быть менее 7 символов. Он может не соответствовать паролю учетной записи MSA или домена.софт или домена.
6. Щелкните **Pair** (Связать), чтобы подключиться к порталу устройств Windows на устройстве HoloLens.

Чтобы изменить это имя пользователя или пароль, повторите этот процесс, посетив страницу безопасности устройства по адресу https://<IP-адрес вашего устройства HoloLens>/devicepair.htm.

## <a name="security-certificate"></a>Сертификат безопасности

Если вы видите в браузере ошибку сертификата, можно исправить ее, создав доверительное отношение с устройством.

Каждое устройство HoloLens создает собственный самозаверяющий сертификат для своего SSL-соединения. По умолчанию веб-браузер на вашем ПК не доверяет этому сертификату, и вы можете получить «ошибку сертификата». Скачав этот сертификат с вашего устройства HoloLens (по USB или доверенной сети Wi-Fi) и настроив доверие к нему на своем ПК, можно безопасно подключаться к устройству.
1. **Убедитесь, что вы работаете в безопасной сети (USB или сеть Wi-Fi, которой вы доверяете).**
2. Скачайте сертификат устройства со страницы "Безопасность" на портале устройств.
   * Откройте страницу https://<IP-адрес вашего устройства HoloLens>/devicepair.htm.
   * Разверните узел System > Preferences (Система > Настройки). 
   * Прокрутите вниз до элемента Device Security (Безопасность устройства) и нажмите кнопку Download this device's certificate (Скачать сертификат этого устройства).
3. Установите сертификат в хранилище "Доверенные корневые центры сертификации" на вашем компьютере.
   * В меню "Пуск" Windows введите строку "Управление сертификатами компьютеров" и запустите соответствующее приложение.
   * Разверните папку **Доверенные корневые центры сертификации**.
   * Выберите папку **Сертификаты**.
   * В меню "Действие" выберите: Все задачи > Импорт...
   * Выполните мастер импорта сертификатов, используя файл сертификата, загруженные с Портала устройств.
4. Перезапустите браузер.

>[!NOTE]
> Этот сертификат будет доверенным только для этого устройства, и пользователю придется снова повторить процесс в случае установки нового образа на устройстве.

## <a name="sideloading-applications"></a>Загрузка неопубликованных приложений

### <a name="installing-a-certificate"></a>Установка сертификата

1. На портале устройств Windows перейдите на страницу **Apps manager** (Диспетчер приложений).
2. В разделе Deploy apps (Развертывание приложений) выберите **Install Certificate** (Установить сертификат).
3. В разделе Select certificate file (.cer) used to sign app package (Выбрать CER-файл сертификата, использовавшийся для подписывания пакета приложения) щелкните Choose File (Выбрать файл) и перейдите к сертификату, который связан с загружаемым пакетом приложения.
4. Нажмите кнопку **Установить**, чтобы начать установку.

![Снимок экрана: страница диспетчера приложений на портале устройств Windows](images/sideloading-1.png)

### <a name="installing-an-app"></a>Установка приложения

> [!NOTE]
> Чтобы успешно установить приложение через портал устройств, его нужно подписать сертификатом, который предварительно должен быть установлен на устройстве. Инструкции см. в [предыдущем разделе](#installing-a-certificate).

1. После [создания пакета приложения в Visual Studio](using-visual-studio.md) вы можете удаленно установить его на устройстве из созданных файлов:

![Снимок экрана: содержимое файла пакета приложения](images/sideloading-2.png)

2. На портале устройств Windows перейдите на страницу **Apps manager** (Диспетчер приложений).
3. В разделе **Deploy apps** (Развертывание приложений) выберите **Local Storage** (Локальное хранилище).
4. В разделе Select the application package (Выбор пакета приложения) щелкните Choose File (Выбрать файл) и найдите пакет неопубликованного приложения, который вы намерены загрузить.
5. Установите соответствующие флажки, если вы хотите установить необязательные пакеты или пакеты платформы вместе с приложением, и щелкните **Next** (Далее):

![Снимок экрана: страница диспетчера приложений на портале устройств Windows с выделенной вкладкой Local Storage (Локальное хранилище)](images/sideloading-3.png)

6. Нажмите кнопку **Установить**, чтобы начать установку.
 
![Снимок экрана: страница диспетчера приложений на портале устройств Windows с данными об успешной установке](images/sideloading-4.png) 

После завершения установки вернитесь на страницу **All apps** (Все приложения) на HoloLens и запустите установленное приложение.

## <a name="device-portal-pages"></a>Страницы Портала устройств

### <a name="home"></a>Главная

![Главная страница портала устройств Windows для Microsoft HoloLens](images/using-windows-portal-img-04.png)<br>
*Главная страница портала устройств Windows для Microsoft HoloLens*

> [Примечание] Параметры, настроенные на портале устройств, применяются ко всему устройству и сохраняются при перезапуске. Портал устройств рекомендуется использовать только при разработке, но не на развернутых устройствах.

Ваш сеанс на портале устройств начинается на Главной странице. Откройте другие страницы на панели навигации вдоль левого края главной страницы.

Панель инструментов в верхней части страницы предоставляет доступ к часто используемому состоянию и функциям.
* **Online** (Подключено): указывает, подключено ли устройство к Wi-Fi.
* **Shutdown** (Завершение работы): отключает устройство.
* **Restart** (Перезапуск): выключает и включает питание на устройстве.
* **Security** (Безопасность): открывает страницу "Безопасность устройства".
* **Cool** (Холодный): указывает температуру устройства.
* **A/C** (Питание): указывает, подключено ли устройство к источнику электропитания и заряжается ли оно.
* **Help** (Справка): открывает страницу документации по интерфейсу REST.

На главной странице отображаются следующие сведения:
* **Device Status** (Состояние устройства): отслеживает работоспособность устройства и сообщает о критических ошибках.
* **Windows information** (Сведения об ОС Windows): отображает имя устройства HoloLens и установленную версию Windows.
* Раздел **Настройки** содержит следующие параметры:
   * **IPD** (Межзрачковое расстояние): задает межзрачковое расстояние, то есть расстояние в миллиметрах между центрами зрачков смотрящего прямо пользователя. Этот параметр незамедлительно вступает в силу. Значение по умолчанию было вычислено автоматически при настройке устройства.
   * **Device name** (Имя устройства): присвойте имя устройству HoloLens. Перезапустите устройство после изменения этого параметра, чтобы новое значение вступило в силу. После нажатия **Save** (Сохранить) появится диалоговое окно с вопросом о немедленной перезагрузке устройства или отложенной перезагрузке.
   * **Sleep settings** (Параметры спящего режима): позволяют настроить длительность времени ожидания перед переходом устройства в спящий режим при наличии питания от сети или при питании от аккумулятора.

### <a name="3d-view"></a>Трехмерное представление

![Страница трехмерного представления на портале устройств Windows для Microsoft HoloLens](images/using-windows-portal-img-05.png)<br>
*Страница трехмерного представления на портале устройств Windows для Microsoft HoloLens*

Используйте страницу «Трехмерное представление», чтобы оценить, как HoloLens воспринимает ваше окружение. В этом представлении можно перемещаться с помощью мыши:
* Повернуть: левый щелчок + мышь;
* Сдвиг: правый щелчок + мышь;
* Масштабирование: прокрутка мышью.
* **Tracking options** (Параметры отслеживания изменений)
   * включение непрерывного визуального отслеживания посредством установки флажка **Force visual tracking** (Принудительное визуальное отслеживание). 
   * **Pause** (Пауза): останавливает визуальное отслеживание.
* **View options** (Параметры представления): позволяет задать приведенные ниже параметры трехмерного представления.
  * **Tracking** (Отслеживание): определяет, используется ли визуальное отслеживание.
  * **Show floor** (Показать пол): отображение плоскости пола "в клеточку".
  * **Show frustum** (Показать усеченную пирамиду): отображение усеченной пирамиды представления.
  * **Show stabilization plane** (Показать плоскость стабилизации): отображение плоскости, используемой HoloLens для стабилизации движения.
  * **Show mesh** (Показать сетку): отображение сетки пространственного картирования, которая представляет ваше окружение.
  * **Show spatial anchors** (Показать пространственные привязки): отображение пространственных привязок для активного приложения. Для получения и обновления привязок нажмите кнопку Update (Обновить).
  * **Show details** (Показать детали): отображение положения рук, кватернионов поворота головы, а также исходного вектора устройства по мере их изменения в реальном времени.
  * **Full screen button** (Кнопка "Полный экран"): отображение трехмерного представления в полноэкранном режиме. Нажмите клавишу ESC, чтобы выйти из полноэкранного режима.
* **Surface reconstruction** (Реконструкция поверхности): Коснитесь кнопки **Update** (Обновить) для отображения последней сетки пространственного картирования с этого устройства. Выполнение полного прохода может занять некоторое время, иногда до нескольких секунд. В трехмерном представлении сетка не обновляется автоматически, и вам необходимо вручную щелкнуть **Update** (Обновить), чтобы получить с устройства последнюю сетку. Щелкните **Save** (Сохранить), чтобы сохранить текущую сетку пространственного картирования в виде OBJ-файла на локальном компьютере.
* **Spatial anchors** (Пространственные привязки): щелкните Update (Обновить), чтобы отобразить или обновить пространственные привязки для активного приложения.

### <a name="map-manager"></a>Диспетчер карт

Диспетчер карт позволяет передавать между устройствами карты, которые затем можно использовать для настройки общих взаимодействий для клиентов, предоставляющих развлекательные услуги в специально оборудованных местах. Это средство позволяет импортировать и экспортировать системные карты и привязки.  

Чтобы получить доступ к диспетчеру карт, войдите на портал устройств и выберите **Смешанная реальность -> Диспетчер карт**: 

![Страница диспетчера карт на портале устройств Windows](images/using-windows-portal-img-06.png)
*Страница диспетчера карт на портале устройств Windows в Microsoft HoloLens*

#### <a name="exporting-and-importing-maps"></a>Экспорт и импорт карт

Чтобы экспортировать карты, щелкните **Export System Map & Anchors** (Экспортировать системные карты и привязки). Это может занять некоторое время, поэтому будьте готовы, что карта будет экспортироваться 30–60 секунд. По завершении файл будет скачан в браузере.  

Чтобы импортировать карты и привязки, щелкните **Upload a map file** (Отправить файл карты) и **Upload an anchor file** (Отправить файл привязки), соответственно, затем выберите ранее экспортированный файл карты или привязки. Отправленный файл карты или привязки мог быть получен с любого другого устройства HoloLens. 

> [!NOTE]
> В HoloLens также можно импортировать и экспортировать базу данных пространственного сопоставления. Но для других устройств (не HoloLens) такая возможность недоступна.  


### <a name="mixed-reality-capture"></a>Смешанный захват реальности

![Страница приложения "Съемка смешанной реальности" на портале устройств Windows для Microsoft HoloLens](images/using-windows-portal-img-07.png)<br>
*Страница приложения "Съемка смешанной реальности" на портале устройств Windows для Microsoft HoloLens*

> [!IMPORTANT]
> Параметры, настроенные на портале устройств, применяются ко всему устройству и сохраняются при перезапуске. Все параметры, измененные на портале устройств, будут применяться к захватам и приложениям смешанной реальности. Используйте портал устройств только при разработке, а не для приложений, развернутых в организации.

Используйте страницу «Смешанный захват реальности», чтобы сохранить мультимедийные потоки для устройства HoloLens.
* **Capture Settings** (Параметры захвата): управляйте захватываемыми мультимедийными потоками с помощью приведенных ниже параметров.
  * **Holograms** (Голограммы): захват голографического содержимого в видеопотоке. Голограммы обрабатываются в режиме моно, а не стерео.
  * **PV camera** (Фото- или видеокамера): захват видеопотока с фото- или видеокамеры.
  * **Mic Audio** (Звук микрофона): захват звука с микрофона.
  * **App Audio** (Звук приложения): захват звука из работающего сейчас приложения.
  * **Render from Camera** (Отрисовка с камеры): сопоставляет захват с положением фото- или видеокамеры, если это [поддерживается запущенным приложением](mixed-reality-capture-overview.md#render-from-the-pv-camera-opt-in) (только для HoloLens 2).
  * **Live preview quality** (Качество предварительного просмотра в реальном времени): выберите разрешение экрана, частоту кадров и скорость потоковой передачи для предварительного просмотра в реальном времени.
* **Audio Settings** (Параметры звука) (только для HoloLens 2):
  * **Audio Media Category** (Категория звукового мультимедиа): выберите категорию, которая будет использоваться при обработке звука с микрофона. Вариант **Default** (По умолчанию) предусматривает частичное сохранение фонового шума, а вариант **Communications** (Передача) — полное подавление.
  * **App Audio Gain** (Усиление звука приложения): степень понижения или повышения громкости звука приложения.
  * **Mic Audio Gain** (Усиление микрофона): степень понижения или повышения громкости звука с микрофона.
* **Photo and Video Settings** (Параметры фотосъемки и видеозаписи) (HoloLens 2, версия 2004 и выше):
  * **Capture Profile** (Профиль съемки): выберите профиль, используемый для фотосъемки и видеозаписи. Профиль определяет доступные значения разрешения и частоты кадров.
  * **Photo Resolution** (Разрешение фото): разрешение, с которым будут делаться снимки.
  * **Video Resolution and Frame-rate** (Разрешение и частота кадров видео): разрешение и частота кадров, с которыми будет записываться видео.
  * **Video Stabilization Buffer** (Буфер стабилизации видео): размер буфера, используемого при записи видео. Чем больше это значение, тем лучше будет работать компенсация быстрых движений.
* Нажмите кнопку **Live preview** (Предварительный просмотр в режиме реального времени), чтобы показать захваченный поток. Кнопка **Stop live preview** (Остановить предварительный просмотр в реальном времени) останавливает захваченный поток.
* Выберите элемент **Record** (Запись), чтобы начать запись потока смешанной реальности с использованием указанных параметров. **Stop recording** (Остановить запись) приводит к завершению и сохранению записи.
* Выберите элемент **Take photo** (Сделать снимок), чтобы создать статическое изображение из захваченного потока.
* Нажмите кнопку **Restore Default Settings** (Восстановить параметры по умолчанию), чтобы восстановить заданные по умолчанию параметры звука, фотосъемки и видеозаписи.
* **Videos and photos** (Видео и фотографии): отображение списка видео и фотографий, снятых на это устройство.

Все параметры на этой странице применяются к записям, созданным с помощью портала устройств Windows. Некоторые из них применяются также к системным файлам смешанного захвата реальности, например меню "Пуск", аппаратные кнопки, глобальные голосовые команды, Miracast и пользовательские средства смешанного захвата реальности.

|  Параметр  |  Действует для системных средств MRC  |  Действует для пользовательских средств MRC |
|----------|----------|----------|
|  Holograms (Голограммы)  |  Нет  |  Нет |
|  PV camera (Фото- и видеокамера)  |  Нет  |  Нет |
|  Mic Audio (Звук микрофона)  |  Нет  |  Нет |
|  App Audio (Звук приложения)  |  Нет  |  Нет |
|  Render from Camera (Отрисовка с камеры)  |  Да    |  Да (с возможностью переопределения) |
|  Live preview quality (Качество предварительного просмотра в реальном времени)  |  Нет  |  Нет |
|  Audio Media Category (Категория звукового мультимедиа)  |  Да  |  Нет |
|  App Audio Gain (Усиление звука приложения)  |  Да  |  Да (с возможностью переопределения) |
|  Mic Audio Gain (Усиление микрофона)  |  Да  |  Да (с возможностью переопределения) |
|  Capture Profile (Профиль съемки)  |  Да  |  Нет |
|  Photo Resolution (Разрешение фото)  |  Да  |  Нет |
|  Video Resolution and Frame-rate (Разрешение и частота кадров видео)  |  Да  |  Нет |
|  Video Stabilization Buffer (Буфер стабилизации видео)  |  Да  |  Да (с возможностью переопределения) |

> [!NOTE]
> Существуют следующие [ограничения для одновременных MRC](../advanced-concepts/mixed-reality-capture-overview.md#simultaneous-mrc-limitations):
> * Если приложение пытается обращаться к фото- или видеокамере в то время, когда портал устройств Windows записывает видео, эта запись видео прерывается.
>   * HoloLens 2 не будет прерывать запись видео, если приложение обращается к фото- или видеокамере в режиме SharedReadOnly.
> * Если приложение активно использует фото- или видеокамеру, портал устройств Windows сможет выполнить фото- или видеосъемку.
> * Потоковая трансляция.
>   * HoloLens (1-го поколения) не позволяет приложению обращаться к фото- или видеокамере во время потоковой трансляции с портала устройств Windows.
>   * HoloLens (1-го поколения) не может выполнять потоковую трансляцию, если приложение активно использует фото- или видеокамеру.
>   * HoloLens 2 автоматически останавливает потоковую трансляцию при попытке приложения обратиться к фото- или видеокамере в режиме ExclusiveControl.
>   * HoloLens 2 сможет запустить потоковую трансляцию, когда приложение активно использует фото- или видеокамеру.

### <a name="performance-tracing"></a>Трассировка производительности

![Страница трассировки производительности на портале устройств Windows для Microsoft HoloLens](images/using-windows-portal-img-08.png)<br>
*Страница трассировки производительности на портале устройств Windows для Microsoft HoloLens*

Захват трассировок с помощью [Windows Performance Recorder](/previous-versions/windows/it-pro/windows-8.1-and-8/hh448205(v=win.10)) (WPR) с устройства HoloLens.
* **Available profiles** (Доступные профили): выберите профиль WPR в раскрывающемся списке, затем выберите элемент **Start** (Запуск) для начала трассировки.
* **Custom profiles** (Пользовательские профили): Нажмите кнопку **Browse** (Обзор) для выбора профиля WPR на своем компьютере. Выберите элемент **Upload and start** (Передать и запустить), чтобы начать трассировку.

Чтобы прекратить трассировку, щелкните ссылку остановки. Оставайтесь на этой странице до тех пор, пока файл трассировки не будет полностью скачан.

Захваченные файлы ETL можно открыть для анализа в [Windows Performance Analyzer](/previous-versions/windows/it-pro/windows-8.1-and-8/hh448170(v=win.10)).

### <a name="processes"></a>Процессы

![Страница процессов на портале устройств Windows для Microsoft HoloLens](images/using-windows-portal-img-09.png)<br>
*Страница процессов на портале устройств Windows для Microsoft HoloLens*

Отображаются сведения о выполняемых в настоящее время процессах. Сюда входят приложения и системные процессы.

### <a name="system-performance"></a>Производительность системы

![Страница производительности системы на портале устройств Windows для Microsoft HoloLens](images/using-windows-portal-img-10.png)<br>
*Страница производительности системы на портале устройств Windows для Microsoft HoloLens*

Отображение в реальном времени графиков системной диагностической информации, таких как использование питания, частота кадров и загрузка ЦП.

Ниже приведены доступные метрики:
* **SoC power** (Питание системы на кристалле): мгновенное потребление питания системой на кристалле, с усреднением за одну минуту.
* **System power** (Питание системы): мгновенное потребление питания системой, с усреднением за одну минуту.
* **Frame rate** (Частота кадров): кадры в секунду, пропущенные VBlank в секунду и последующие пропущенные VBlank.
* **GPU**: использование модуля GPU, в процентах от общей доступной производительности.
* **ЦП**: доступность в процентах от общего значения.
* **I/O** (Ввод-вывод): операции чтения и записи.
* **Сеть**: получение и отправка данных.
* **Memory** (Память): всего, используется, доступно, выделено, выгружаемая, невыгружаемая.

### <a name="apps"></a>Приложения

![Страница приложений на портале устройств Windows для Microsoft HoloLens](images/using-windows-portal-img-11.png)<br>
*Страница приложений на портале устройств Windows для Microsoft HoloLens*

Управляет приложениями, которые установлены на HoloLens.
* **Installed apps** (Установленные приложения): удаление и запуск приложений.
* **Running apps** (Запущенные приложения): отображение всех работающих в настоящее время приложений.
* **Install app** (Установить приложение): выбор в папке на компьютере или в сети пакетов приложений для установки.
* **Dependency** (Зависимость): добавление зависимостей для устанавливаемого приложения.
* **Deploy** (Развертывание): развертывание выбранного приложения и его зависимостей на устройстве HoloLens.

### <a name="app-crash-dumps"></a>Аварийные дампы для приложения

![Страница аварийных дампов для приложения на портале устройств Windows для Microsoft HoloLens](images/using-windows-portal-img-12.png)<br>
*Страница аварийных дампов для приложения на портале устройств Windows для Microsoft HoloLens*

На этой странице можно собирать дампы сбоев для загрузки в сторонние приложения. Установите флажок **Crash Dumps Enabled** (Аварийные дампы включены) для каждого приложения, в котором следует собирать аварийные дампы. Вернитесь на эту страницу для сбора дампов сбоев. Файлы дампов можно [открыть для отладки в Visual Studio](/previous-versions/visualstudio/visual-studio-2015/debugger/using-dump-files).

### <a name="file-explorer"></a>Проводник

![Страница проводника на портале устройств Windows для Microsoft HoloLens](images/using-windows-portal-img-13.png)<br>
*Страница проводника на портале устройств Windows для Microsoft HoloLens*

Этот проводник позволяет просматривать, отправлять и скачивать файлы. Вы можете работать с файлами в папках Documents (Документы) и Pictures (Изображения), а также в папках локального хранилища для тех файлов, которые развернуты из Visual Studio или с портала устройств.

### <a name="kiosk-mode"></a>Режим полного экрана

>[!NOTE]
>Полноэкранный режим доступен только в [Microsoft HoloLens Commercial Suite](/hololens/hololens-commercial-features).

![Страница полноэкранного режима на портале устройств Windows в Microsoft HoloLens](images/using-windows-portal-img-14.png)

Изучите статью [Настройка устройства HoloLens в режиме киоска](/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) в Центре Майкрософт для ИТ-специалистов, чтобы получить актуальные инструкции по включению режима киоска на портале устройств Windows.

### <a name="logging"></a>Ведение журнала

![Страница ведения журналов на портале устройств Windows для Microsoft HoloLens](images/using-windows-portal-img-15.png)<br>
*Страница ведения журналов на портале устройств Windows для Microsoft HoloLens*

Управление трассировкой событий Windows (ETW) в реальном времени на устройстве HoloLens.

Установите флажок **Hide providers** (Скрыть поставщики), чтобы отображался только список **Events** (События).
* **Registered providers** (Зарегистрированные поставщики): выберите поставщик ETW и уровень трассировки. Уровень трассировки — это одно из следующих значений:
   1. ненормальный выход или прекращение;
   2. серьезные ошибки;
   3. Предупреждения
   4. предупреждения, не связанные с ошибками.

Выберите элемент **Enable** (Включить), чтобы начать трассировку. Поставщик добавляется в раскрывающийся список **Включенные поставщики**.
* **Custom providers** (Настраиваемые поставщики): выберите пользовательский поставщик ETW и уровень трассировки. Определите поставщика по его GUID. Не включайте скобки в GUID.
* **Enabled providers** (Включенные поставщики): выводит список включенных поставщиков. Выберите поставщика в раскрывающемся списке и щелкните или нажмите **Отключить**, чтобы остановить трассировки. Щелкните или нажмите **Стоп**, чтобы приостановить всю трассировку.
* **Providers history** (Журнал поставщиков): отображение поставщиков ETW, которые были включены во время текущего сеанса. Щелкните или нажмите **Включить**, чтобы активировать поставщика, который ранее был отключен. Щелкните или нажмите **Очистить**, чтобы очистить журнал.
* **Events** (События): список событий ETW для выбранных поставщиков в формате таблицы. Эта таблица обновляется в режиме реального времени. Под этой таблицей нажмите кнопку **Очистить**, чтобы удалить из нее все события трассировки событий Windows. Это не приводит к отключению поставщиков. Вы можете щелкнуть **Сохранить в файл**, чтобы экспортировать собранные события трассировки событий Windows локально в CSV-файл.
* **Filters** (Фильтры): позволяет отфильтровать события ETW по идентификатору, ключевому слову, уровню, имени поставщика, имени задачи или фразе. Вы даже можете сочетать несколько критериев по следующими правилам:
   1. Если критерии относятся к одному свойству, отображаются события, соответствующие любому из критериев.
   2. Если критерии относятся к разным свойствам, отображаются события, соответствующие всем критериям одновременно.

Например, вы можете указать критерий *(Task Name содержит Foo или Bar) AND (Text содержит error или warning)*

### <a name="simulation"></a>Simulation

![Страница имитации на портале устройств Windows для Microsoft HoloLens](images/using-windows-portal-img-16.png)<br>
*Страница имитации на портале устройств Windows для Microsoft HoloLens*

Позволяет записывать и воспроизводить входные данные для тестирования.
* **Capture room** (Захват комнаты): используется для скачивания файла моделирования комнаты, который содержит сетку пространственного картирования для окружения пользователя. Присвойте комнате имя, затем щелкните **Capture** (Захват) для сохранения данных в формате XEF-файла на локальном компьютере. Этот файл комнаты может быть загружен в эмулятор HoloLens.
* **Recording** (Запись): выберите потоки для записи, присвойте записи имя и нажмите кнопку **Record** (Запись), чтобы начать запись. Выполняйте действия с помощью устройства HoloLens, затем щелкните **Stop** (Стоп), чтобы сохранить XEF-файл на локальном компьютере. Этот файл может быть загружен в эмулятор или на устройство HoloLens.
  >[!NOTE]
  >В настоящее время функция записи доступна только на HoloLens 1-го поколения. Запись пока не поддерживается на HoloLens 2, но поддерживается воспроизведение существующих записей.
* **Playback** (Воспроизведение): нажмите кнопку **Upload recording** (Отправить запись) для выбора XEF-файла на компьютере и отправки данных на устройство HoloLens.
* **Control mode** (Режим управления): выберите в раскрывающемся списке **Default** (По умолчанию) или **Simulation** (Имитация), а затем нажмите кнопку **Set** (Задать) для выбора режима на устройстве HoloLens. Выбор «Симуляторы» отключает датчики на устройстве HoloLens и использует вместо них переданные смоделированные данные. Если переключиться в режим Simulation (Симуляция), устройство HoloLens не будет реагировать на действия реального пользователя, пока не будет восстановлен режим Default (По умолчанию).

### <a name="networking"></a>сеть;

![Страница сети на портале устройств Windows для Microsoft HoloLens](images/using-windows-portal-img-17.png)<br>
*Страница сети на портале устройств Windows для Microsoft HoloLens*

Управление подключениями через Wi-Fi на устройстве HoloLens.
* **WiFi adapters** (Адаптеры Wi-Fi): выберите адаптер Wi-Fi и профиль в раскрывающихся списках. Нажмите кнопку **Connect** (Подключиться), чтобы применить выбранный адаптер.
* **Available networks** (Доступные сети): вывод списка сетей Wi-Fi, к которым может подключиться HoloLens. Нажмите кнопку **Refresh** (Обновить), чтобы обновить список.
* **IP configuration** (Конфигурация IP): отображение IP-адреса и других сведений о сетевом подключении.

### <a name="virtual-input"></a>Виртуальный ввод

![Страница виртуального ввода на портале устройств Windows для Microsoft HoloLens](images/using-windows-portal-img-18.png)<br>
*Страница виртуального ввода на портале устройств Windows для Microsoft HoloLens*

Отправляет клавиатурный ввод с удаленного компьютера на устройство HoloLens.

Щелкните область (или коснитесь ее) под **виртуальной клавиатурой**, чтобы включить отправку нажатий клавиш на устройство HoloLens. Введите текст в текстовом поле **Input text** (Ввод текста), затем нажмите кнопку **Send** (Отправить), чтобы передать нажатия клавиш в активное приложение.

## <a name="device-portal-rest-apis"></a>Интерфейсы REST API для портала устройств

Весь портал устройств построен на основе [интерфейсов REST API](device-portal-api-reference.md), которые можно использовать для доступа к данным и управления устройством программным способом.

## <a name="troubleshooting"></a>Устранение неполадок

### <a name="how-to-fix-the-its-lonely-here-message"></a>Исправление ошибки, из-за которой появляется сообщение "Здесь ничего нет"

> [!NOTE]
> Переход с HoloLens 2 на HoloLens (1-го поколения) может привести к отображению пустых страниц, если сначала использовалась версия HoloLens 2, а не HoloLens 1-го поколения.

![Сообщение "Здесь ничего нет" на странице портала устройств](images/using-windows-portal-img-19.png)

1. В меню слева сверху выберите **Сбросить макет**.

![Выбор элемента "Сбросить макет" в меню портала устройств](images/using-windows-portal-img-20.png)

2. Щелкните **Сбросить макет** под заголовком **Reset workspace** (Сброс рабочей области). Страница портала автоматически обновится, и на ней отобразится содержимое.

![Выбор элемента "Сбросить макет" на странице сброса настроек рабочей области](images/using-windows-portal-img-21.png)