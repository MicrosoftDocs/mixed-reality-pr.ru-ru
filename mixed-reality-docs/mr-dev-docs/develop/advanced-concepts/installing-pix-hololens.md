---
title: Установка PIX для HoloLens 2
description: узнайте, как установить PIX для устройств HoloLens 2.
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: HoloLens, HoloLens 2, PIX, capture, гарнитура смешанной реальности, гарнитура windows mixed reality, гарнитура виртуальной реальности
ms.openlocfilehash: 29cb741cd986fbb98dabb1faf2051450fd0286c3
ms.sourcegitcommit: bea83261bf9ce7a27a618e5bc54dc4d7711f5435
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2021
ms.locfileid: "130157985"
---
# <a name="installing-pix-for-hololens-2"></a>Установка PIX для HoloLens 2

[PIX](https://devblogs.microsoft.com/pix) — это средство настройки и отладки производительности для приложений DirectX 12 на Windows. 

## <a name="setup"></a>Настройка

1. загрузите последнюю [версию PIX с]( https://devblogs.microsoft.com/pix/download) главного компьютера и подключите HoloLens 2 к компьютеру через USB-кабель.

2. если HoloLens 2 входит в [сборку предварительной оценки Windows](https://insider.windows.com) или имеет конфигурацию, которая отменяет PIX, переносит [устройство](/hololens/hololens-recovery) на удаление всех данных.

3. Включить **режим разработчика** и **портал устройств**:

* откройте **Параметры** из дома смешанной реальности:

![снимок экрана: меню "HoloLens" с выделенной кнопкой "параметры"](images/pix-img-01.jpg)

* Выберите **обновление & безопасность**:

![снимок экрана: окно "параметры" открыто на HoloLens с выделенной кнопкой "обновить" и "безопасность"](images/pix-img-02.jpg)

* Выберите **для разработчиков**:

![Снимок экрана: окно "безопасность и обновления" с выделенной кнопкой "для разработчиков"](images/pix-img-03.jpg)

* Включение **использования функций разработчика** и **Включение портала устройств**

![Снимок экрана для окна "разработчики" в окне "Параметры" с выделенной кнопкой "включить на портале устройства"](images/pix-img-04.jpg)

![Снимок экрана: окно "для разработчиков" открыто в меню "параметры с помощью переключателя" Разработка компонентов "](images/pix-img-05.jpg)

* Когда устройство по-прежнему подключено, находится в спящем режиме и пользователь вошел в систему, запустите Visual Studio.

> [!IMPORTANT]
> Убедитесь, что устройство находится не в режиме ожидания или в спящем режиме. если у вас возникли проблемы с этим шагом, обратитесь к [инструкциям на портале устройств Windows](./using-the-windows-device-portal.md).

## <a name="preparing-for-deployment"></a>Подготовка к развертыванию

1. в Visual Studio задайте **ARM64** в качестве платформы и **устройства** в качестве устройства:

![Снимок экрана решения Visual Studios с выделенными параметрами платформы и устройства](images/pix-img-06.png)

2. когда Visual Studio запрашивает у устройства **пин-код** :

![Снимок экрана всплывающего окна Visual Studio с запросом ПИН-кода](images/pix-img-07.png)

* выберите **Параметры** из оболочки
* Выберите **обновление & безопасность**
* Выберите **для разработчиков** и нажмите пару в разделе **обнаружение устройства** 

![Снимок экрана для окна "разработчики", Открытый в параметрах с выделенным обнаружением устройств](images/pix-img-08.jpg)

![Снимок экрана: всплывающее окно платного устройства с выделенным кодом регистрации](images/pix-img-09.jpg)

* Введите созданный ПИН-код в Visual Studio

3. Visual Studio развернет приложение на подключенном HoloLens 2, что может занять несколько минут в зависимости от приложения.

## <a name="launching-pix"></a>Запуск PIX

Сначала используйте портал устройств, чтобы убедиться, что приложение не выполняется на HoloLens 2. Затем запустите PIX, подключитесь к устройству и выберите **Домашняя страница**:

![Снимок экрана с начальным экраном приложения PIX](images/pix-img-10.png)

* выберите **Подключение** в меню слева:

![Снимок экрана: меню в левой части приложения PIX с выделенной кнопкой "подключить"](images/pix-img-11.png)

2. На вкладке **компьютер** выберите **Добавить** и введите следующие учетные данные:
    * Псевдоним: по усмотрению пользователя
    * Имя узла или IP-адрес: 127.0.0.1

3. выберите **Подключение** в правом нижнем углу вкладки **компьютер** :

![Снимок экрана: окно подключения приложения PIX с псевдонимом, именем узла, IP-адресом и выделенной кнопкой "Добавить"](images/pix-img-12.png)

> [!NOTE]
> Первое соединение всегда выполняется медленнее, так как копируются двоичные файлы.

4. когда PIX подключается к HoloLens 2, найдите свое приложение в разделе **выбор целевого процесса** на вкладке запуск UWP и выберите **запуск**:

![Снимок экрана приложения PIX с выделенным окном "Выбор целевого процесса" и "Запуск"](images/pix-img-13.png)

## <a name="gpu-captured"></a>Записываемый GPU

1. Запустите захват GPU, щелкнув **фото** в разделе " **запись GPU** ":

![Снимок экрана приложения PIX с выделенной панелью подключения к ГРАФИЧЕСКОМу набору данных](images/pix-img-14.png)

2. Откройте запись для анализа, щелкнув созданный снимок экрана на панели **захвата GPU** :

![Снимок экрана приложения PIX с выделенным фрагментом графического процессора (панель захвата GPU)](images/pix-img-15.png)

3. Чтобы начать анализ, нажмите кнопку " **Пуск** ":

![Снимок экрана приложения PIX, выделенного кнопкой "запустить"](images/pix-img-16.png)

> [!IMPORTANT]
> Если сбор данных о времени выполняется после записи GPU, потребуется перезагрузить гарнитуру. Это одноразовый перезапуск устройства, необходимый для сбора данных о времени.

Теперь PIX готов к использованию.

## <a name="see-also"></a>См. также раздел
* [Домашняя страница PIX](https://devblogs.microsoft.com/pix)