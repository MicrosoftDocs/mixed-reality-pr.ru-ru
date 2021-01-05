---
title: Минимальные рекомендации по совместимости Windows Mixed Reality с оборудованием ПК
description: В диаграмме расструктурированы минимальные требования к системе ПК для обеспечения совместимости с Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, Смешанная реальность, виртуальная реальность, VR, MR, Ultra, совместимая, совместимость, требования к системе, ПК
appliesto:
- Windows 10
ms.openlocfilehash: bd287e2089056be56330c2c2e8e9af2c079009ac
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725665"
---
# <a name="windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines"></a>Минимальные рекомендации по совместимости Windows Mixed Reality с оборудованием ПК

## <a name="features-and-experiences"></a>Функции и возможности

Windows 10 поддерживает Windows Mixed Reality и Windows Mixed Reality Ultra. Какая версия зависит от оборудования компьютера.

В Windows Mixed Reality вы получаете ряд дополнительных возможностей и функций:

* Более четкие визуальные элементы и частота обновления (90 кадров в секунду).
* Больше приложений и возможностей, включая наиболее интенсивные графические игры.
* Окно "" зеркального отображения "" на рабочем столе, которое показывает, что отображается в смешанной реальности.
* Записывайте и Делитесь видеороликами и фотографиями ваших возможностей смешанной реальности.

## <a name="minimum-pc-hardware-guidelines"></a>Минимальные рекомендации по оборудованию ПК

Для лучшего опыта работы с Windows Mixed Reality Начните с нового компьютера, [готового Windows Mixed Reality](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) , или компьютера, совместимого с Windows Mixed Reality, который может обеспечить высокую производительность Windows Mixed Reality. Windows Mixed Reality Ultra предоставляет более четкие визуальные элементы с более высоким тарифом на обновления, дополнительные возможности приложений, включая наиболее интенсивные графические игры, зеркальное отображение Windows Mixed Reality на рабочем столе, а также возможность записывать и совместно использовать (Фото и видео) ваши впечатления с другими пользователями. 

Ознакомьтесь с рекомендациями по оборудованию и запустите [приложение портала смешанной реальности](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M), чтобы узнать, может ли компьютер работать под управлением Windows Mixed Reality.

Помните, что производительность будет зависеть от конкретной настройки. Кроме того, необходимо убедиться, что ваш ПК имеет [правильные порты](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) для используемой иммерсивного гарнитуры Windows Mixed Reality.

>[!NOTE]
>Рекомендации по разработке компьютеров выше, чем на компьютерах потребителей, использующих приложения смешанной реальности. Если вы являетесь разработчиком смешанной реальности, см. статью [Рекомендуемые спецификации ПК для разработки](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools#immersive_headset_development).


## <a name="mixed-reality-portal-app"></a>Приложение портала смешанной реальности

Портал смешанной реальности — это лучший способ убедиться, что ваш ПК готов к запуску Windows Mixed Reality. 

<a href="https://www.microsoft.com/store/productid/9ng1h8b3zc7m"><img alt="Download Mixed Reality Portal" src="images/WMR-PC-Check-app.png"/></a>

После запуска приложения вы получите одно из следующих сообщений:
* **Все готово.** Ваш ПК занимается выполнением Windows Mixed Reality.
* **Поддерживает некоторые функции.** Этот компьютер может работать под управлением Windows Mixed Reality, но некоторые функции могут быть ограничены.
* **Не удается запустить смешанную реальность.** Этот компьютер не соответствует минимальным требованиям, необходимым для запуска Windows Mixed Reality.

Затем вы получите анализ вашего компьютера в соответствии с требуемым оборудованием, драйверами и операционной системой.
![Снимок экрана: проверка компьютера Windows Mixed Reality](images/screenshot-mr-pc-check.jpg) 

<table>
<tr>
<th>Значок</th><th>Что это означает</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">Ваш компьютер передает требуемый элемент.</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">Возможны проблемы с вашим компьютером для данного требования. Если возникают проблемы, может потребоваться устранение неполадок или обновление компьютера.</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">Ваш компьютер не соответствует требованиям для указанного элемента.</td>
</tr>
</table>

 [Получение справки по результатам портала смешанной реальности](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)

## <a name="compatibility-guidelines"></a>Рекомендации по совместимости
> [!IMPORTANT]
> Мы будем обновлять, доставляя и изменяя эти рекомендации по совместимости компьютеров с Windows Mixed Reality. Регулярно проверяйте последние рекомендации и требования.

**Спецификации совместимых команд HP**<br>
Из-за более высокого разрешения следующие требования применяются к строкам продуктов HP Re & G2, чтобы обеспечить оптимальную работу в 90 Гц, полное разрешение: 

<ul>
<li> Intel Core i5, i7, Intel Xenon E3-1240 V5, что эквивалентно или лучше. Эквивалент или выше AMD ризен 5. </li>
<li> NVIDIA GeForce ГТКС 1080, AMD Radeon RX 5700, эквивалентная или более высокая </li> 
<li> Память: 8 ГБ ОЗУ или больше </li> 
<li> Номер монитора 1x 1,3 </li> 
<li> 1x USB 3,0 Type-C с поддержкой доставки питания (или включенным адаптером питания)</li>
<li> Windows 10 2019 обновление или более поздняя версия </li>
</ul>

**Все остальные ВМР совместимые гарнитуры** <br>
Для всех остальных ХМДС см. следующие требования. 

<table>
<tr>
    <th style="width:10%"></th><th style="vertical-align: middle; text-align: center; width:30%">Портативные компьютеры Windows Mixed Reality</th>
    <th style="vertical-align: middle; text-align: center; width:30%">Компьютеры Windows Mixed Reality</th>
</tr><tr>
    <td style="vertical-align: middle">Операционная система</td><td colspan="2" style="vertical-align: middle; text-align: center;">Windows 10 с обновлением для дизайнеров (RS3) или более поздней версии — Домашняя, профессиональная, Корпоративная, для образовательных учреждений.<br/>    (<b>Примечание</b>. не поддерживается в N версий или Windows 10 Pro в режиме S)</td>
</tr><tr>
    <td style="vertical-align: middle">Процессор</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 4590 (4-го поколения), четырехъядерный (или более эффективный) <br>AMD ризен 5 1400 3.4 ГГц (Настольный), четырехъядерный (или более подходящий)</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 7200U (мобильное поколение с 7-го поколения), Двухъядерная с включенной технологией Intel Hyper-Threading (или выше) <br>AMD ризен 5 1400 3.4 ГГц (Настольный), четырехъядерный (или более подходящий)</td>
</tr><tr>
    <td style="vertical-align: middle">ОЗУ</td>
    <td style="vertical-align: middle; text-align: center;">8 ГБ DDR3 (или более)</td>
    <td style="vertical-align: middle; text-align: center;">8 ГБ двухканальной памяти DDR3 (или выше)</td>
</tr><tr>
    <td style="vertical-align: middle">Свободное пространство на диске</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Не менее 10 ГБ</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Не менее 10 ГБ</td>
</tr><tr>
    <td style="vertical-align: middle">Графическая карта</td>
    <td style="vertical-align: middle; text-align: middle;">
            <ul> 
            <li>NVIDIA ГТКС 1060 (или более поздней версии) дискретный GPU с поддержкой DX12</li>
            <li>Отдельный GPU AMD RX 470/570 (или более поздней версии) с поддержкой DX12 </li>
            </ul>     
            <b>Примечание.</b> GPU должен размещаться в слоте связи PCIe 3,0 X4 + </td>
    <td style="vertical-align: middle; text-align: middle;">
            <li>Встроенный графический процессор Intel HD Graphics 620 (или более поздней версии) с поддержкой DX12 <a href="https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units">(проверяет, больше ли ваша модель)</a></li>
        <li>Дискретный GPU NVIDIA MX150 (или более поздней версии)</li>
        <li>Дискретный GPU NVIDIA GeForce ГТКС 1050</li>
        <li>Дискретный GPU NVIDIA 965M</li>
        <li>AMD Radeon RX 460/560</li>
        </ul>
        <b>Примечание.</b> Более старые графические процессоры Intel, такие как HD Graphics 4xx, 5xx, 2xxx, 3xxx, 4xxx, 5xxx и 6ххх, не поддерживаются.
    </td>
</tr><tr>
    <td style="vertical-align: middle">Драйвер графики</td>
    <td colspan="3" td style="vertical-align: middle; text-align: center;">Модель Windows экранного драйвера (WDDM) 2,2</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">Графический порт изображения</a></td>
    <td style="vertical-align: middle; text-align: center;">HDMI 2,0 или Дисплайпорт 1,2</td>
    <td style="vertical-align: middle; text-align: center;">HDMI 1,4 или Дисплайпорт 1,2</td>
</tr><tr>
    <td style="vertical-align: middle">Отображение</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Подключенный внешний или интегрированный монитор VGA (800x600) (или более высокий)</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">USB-подключение</a></td>
    <td colspan="2" style="vertical-align: middle; text-align: center;">Тип USB 3,0-A </td>
</tr><tr>
    <td style="vertical-align: middle">Подключение Bluetooth (для <a href="controllers-in-wmr.md">контроллеров движения</a>)</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Bluetooth 4,0</td>
</tr><tr>
    <td style="vertical-align: middle">Ожидаемая частота кадров гарнитуры</td>
    <td style="vertical-align: middle; text-align: center;">90 Гц</td>
    <td style="vertical-align: middle; text-align: center;">60 Гц</td>
</tr>
<tr>
    <td style="vertical-align: middle">Питание</td>
    <td style="vertical-align: middle; text-align: center;">Порты USB 3,0 (тип A)</td>
    <td style="vertical-align: middle; text-align: center;">Порты USB 3,0 (тип A)</td>
</tr>
</table>



**Дополнительные сведения:**
* Более крупные Ноутбуки с экраном как минимум 15 "лучше всего.
* Для достижения оптимальной работы мы рекомендуем использовать 8 процессоров Intel® Core™ или 7 для поколения Intel® Core™ i5.
* Гибридные конфигурации графики совместимы только с Windows Mixed Reality Ultra. Дискретный графический адаптер в любой гибридной конфигурации должен соответствовать всем требованиям, перечисленным в руководстве по Windows Mixed Reality для дискретных графических адаптеров.
* Если у вас есть отдельная графическая карта, которая должна работать под управлением Windows Mixed Reality Ultra, но по умолчанию используется частота обновления 60 Гц (кадров 60 в секунду), используйте Дисплайпорт адаптер HDMI 2,0, чтобы подключить гарнитуру и включить частоту обновления 90 Гц.
* Для разных гарнитур могут потребоваться разные аппаратные порты, поэтому убедитесь, что компьютер имеет правильные порты или [необходимые адаптеры](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) для подключения к гарнитуре.

>[!NOTE]
>Отдельное и интегрированное графическое оборудование, которое не соответствует минимальным подтвержденным спецификациям, не было протестировано, подтверждено или оптимизировано для Windows Mixed Reality и может работать неправильно или вообще.

## <a name="windows-mixed-reality-and-surface"></a>Windows Mixed Reality и Surface

Для оптимальной работы Windows Mixed Reality на устройстве Surface рекомендуется использовать Сурфацебук 2 (15), настроенный с NVIDIA GeForce ГТКС 1060 ГБ и 16 ГБ ОЗУ.  Эта конфигурация поддерживает все функции Windows Mixed Reality @ 90 Гц, которые были протестированы и помечены для Windows Mixed Reality Ultra.  В контактной книге 2 (13), Surface Studio, студии Surface и Surface Pro (2017) все функции Windows Mixed Reality настроены с ЦП Intel Core i5 (или выше) и не менее 8 ГБ ОЗУ.

**Требования.**
* Для продуктов Surface требуется, чтобы обновления драйверов были совместимы с Windows Mixed Reality. Эти драйверы можно установить на своем компьютере, перейдя к **параметрам > обновления и безопасности > проверить наличие обновлений**.
* Для устройств Surface требуется [адаптер](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) из видеопортов (Mini ДИСПЛАЙПОРТ или USB-C, в зависимости от компьютера Surface) с HDMI 2,0 для головных телефонов Windows Mixed Reality. Последняя версия Mini-DisplayPort Surface для адаптера HDMI AV совместима с HDMI 2,0 (старая версия не поддерживается). Аналогичным образом, <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">карта USB-C и HDMI</a> также СОВМЕСТИМА с HDMI 2,0.

>[!WARNING]
>Не все Mini Дисплайпорт или USB-C для адаптеров HDMI имеют возможность HDMI 2,0. Попробуйте проверить наличие явной совместимости с "HDMI 2,0" или "4 КБ" на любом адаптере.

Дополнительные сведения о совместимости областей с Windows Mixed Reality доступны в следующей таблице:

<table>
    <tr>
        <th> Устройство Surface </th><th> Поддержка функций Windows Mixed Reality? </th><th> Рекомендуемая конфигурация </th><th> Примечания</th>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Pro (первоначальная) или Surface Pro 2 </td><td style="vertical-align: middle"> None </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Pro 3 </td><td style="vertical-align: middle"> None </td><td> </td><td></td>
    </tr>
(с установленным Windows 10 Pro) <tr>
        <td style="vertical-align: middle"> Surface Pro 4 </td><td style="vertical-align: middle"> None </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface 3 </td><td style="vertical-align: middle"> None </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Book </td><td style="vertical-align: middle"> None </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Контактная книга с базой производительности </td><td style="vertical-align: middle"> None </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Go </td><td style="vertical-align: middle"> None </td><td> </td><td></td>
    </tr>
<tr>
        <td style="vertical-align: middle"> Контактная книга 2 (15 &quot; ) </td><td style="vertical-align: middle"> Полное </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA ГТКС 1060/16 ГБ ОЗУ </td>
        <td>
            <ul>
                <li><b>Рекомендуется</b>. для оптимальной работы Windows Mixed Reality на устройстве Surface рекомендуется использовать сурфацебук 2 15 ", настроенный с NVIDIA GeForce ГТКС 1060 ГБ и 16 ГБ ОЗУ.  Эта конфигурация протестирована и имеет эмблему Windows Mixed Reality Ultra, поэтому она будет поддерживать все функции Windows Mixed Reality и позволит вам использовать самые широко заданный массив совместимых приложений и игр.</li>
                <li>Дискретный GPU NVIDIA GeForce ГТКС 1060 обеспечивает взаимодействие Windows Mixed Reality Ultra @ 90-Гц</li><br/>                <li>Для достижения оптимальной производительности используйте графические драйверы NVIDIA, выпущенные для рабочей книги 2. Новые драйверы могут быть доступны на веб-сайте NVIDIA&#39;s, но не проверяются.</li><br/>                <li>Требуется <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">адаптер HDMI USB-C в качестве адаптера</a> (другие адаптеры могут работать, но не проверяются).</li>
                <li><b>Примечание</b>. Использование DOCKER Surface с контактной книгой 2 официально не поддерживается в Windows Mixed Reality из-за ограничений на источник питания Surface DOCKER.</li><br/>                <li><b>Примечание в Windows 10 версии 1803</b>: если вы&#39;повторное выполнение Windows 10 версии 1803, убедитесь, что вы&#39;Re на сборку ОС 17134,137 или более позднюю версию (устанавливается с помощью KB4284848), чтобы убедиться в наличии последних исправлений производительности. Дополнительные сведения см. в заметках о выпуске для <a href="https://support.microsoft.com/en-us/help/4284848/windows-10-update-kb4284848">KB4284848</a>.</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Контактная книга 2 (13,5 &quot; ) </td><td style="vertical-align: middle"> Частично </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA ГТКС 1050/16 ГБ ОЗУ </td>
        <td>
            <ul>
                <li><b>Примечание</b>. Контактная книга 2 (13) не имеет эмблемы для Windows Mixed Reality, но она поддерживает некоторые функции Windows Mixed Reality, позволяющие использовать ограниченное число совместимых приложений и игр.  Производительность будет зависеть от конфигурации.</li>
                <li>Конфигурации с интегрированным графическим процессором Intel Core i5/Интел HD 620 обеспечивают взаимодействие Windows Mixed Reality @ 60-Гц</li>
                <li>Конфигурация с дискретным графическим процессором Intel Core i7/NVIDIA GeForce ГТКС 1050 обеспечивает опыт работы в Windows Mixed Reality @ 90-Гц</li>                       <li>Для достижения оптимальной производительности используйте графические драйверы NVIDIA, выпущенные для рабочей книги 2. Новые драйверы могут быть доступны на веб-сайте NVIDIA&#39;s, но не проверяются.</li>
                <li>Требуется <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">адаптер HDMI USB-C в качестве адаптера</a> (другие адаптеры могут работать, но не проверяются).</li>
                <li><b>Примечание</b>. Использование DOCKER Surface с контактной книгой 2 официально не поддерживается в Windows Mixed Reality из-за ограничений на источник питания Surface DOCKER.</li>
                <li><b>Примечание в Windows 10 версии 1803</b>: если вы&#39;повторное выполнение Windows 10 версии 1803, убедитесь, что вы&#39;Re на сборку ОС 17134,137 или более позднюю версию (устанавливается с помощью KB4284848), чтобы убедиться в наличии последних исправлений производительности. Дополнительные сведения см. в заметках о выпуске для <a href="https://support.microsoft.com/en-us/help/4284848/windows-10-update-kb4284848">KB4284848</a>.</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Studio </td><td style="vertical-align: middle"> Частично </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA GeForce ГТКС 980m/16 ГБ ОЗУ </td>
        <td>
            <ul>
                <li><b>Примечание</b>. Surface Studio не имеет эмблемы для Windows Mixed Reality, но будет поддерживать некоторые функции Windows Mixed Reality, позволяющие использовать ограниченное число совместимых приложений и игр.  Производительность будет зависеть от конфигурации.</li>
                <li>Конфигурация с NVIDIA GeForce ГТКС 965 m обеспечит взаимодействие Windows Mixed Reality @ 60-Гц.</li>
                <li>Конфигурация с NVIDIA GeForce ГТКС 980 m обеспечит взаимодействие Windows Mixed Reality @ 90-Гц.</li>
                <li>Surface Mini Дисплайпорт to HDMI 2,0 Adapter (другие адаптеры могут работать, но не проверяются).</li>
                <li>Гарнитура Windows Mixed Reality должна быть подключена к USB-порту с помощью символа "+"</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Pro (2017) </td><td style="vertical-align: middle"> Частично </td><td style="vertical-align: middle"> Intel Core i7/Intel® IRI™ плюс график 640/16 ГБ ОЗУ </td>
        <td>
            <ul>
                <li><b>Примечание</b>. Pro Surface (2017) не имеет эмблемы для Windows Mixed Reality, но будет поддерживать некоторые функции Windows Mixed Reality, позволяющие использовать ограниченное число совместимых приложений и игр.  Производительность будет зависеть от конфигурации.</li>
                <li>Конфигурации с интегрированным графическим процессором Intel Core M3/Intel HD 615 <b>не поддерживаются</b></li>
                <li>Конфигурации с интегрированным графическим процессором Intel Core i5/Интел HD 620 обеспечивают взаимодействие Windows Mixed Reality @ 60-Гц</li>
                <li>Конфигурации с интегрированным графическим процессором Intel Core i7/Intel® IRI™ и Graphics 640 будут обеспечивать взаимодействие с Windows Mixed Reality @ 60-Гц</li><br/><li>Требуется мини-Дисплайпорт Surface для устройства HDMI 2,0 (другие адаптеры могут работать, но не проверяются).</li>
                <li>Для <a href="https://support.microsoft.com/en-us/help/4023450/surface-surface-battery-and-power">ползунка производительности</a> требуется задать значение "Лучшая производительность" во время использования</li>
            </ul>
        </td>
    </tr><br/>    <tr>
        <td style="vertical-align: middle"> Ноутбук Surface </td><td style="vertical-align: middle"> Частично </td><td style="vertical-align: middle"> Intel Core i7/Intel® IRI™ плюс график 640/16 ГБ ОЗУ </td>
        <td>
            <ul>
                <li><b>Примечание</b>. Портативный компьютер не имеет эмблемы для Windows Mixed Reality, но будет поддерживать некоторые функции Windows Mixed Reality, позволяющие использовать ограниченное число совместимых приложений и игр.  Производительность будет зависеть от конфигурации.</li>
                <li>Конфигурации с интегрированным графическим процессором Intel Core M3/Intel HD 615 <b>не поддерживаются</b></li>
                <li>Конфигурации с интегрированным графическим процессором Intel Core i5/Интел HD 620 обеспечивают взаимодействие Windows Mixed Reality @ 60-Гц</li>
                <li>Конфигурации с интегрированным графическим процессором Intel Core i7/Intel® IRI™ и Graphics 640 будут обеспечивать взаимодействие с Windows Mixed Reality @ 60-Гц</li><br/><li>Требуется мини-Дисплайпорт Surface для устройства HDMI 2,0 (другие адаптеры могут работать, но не проверяются).</li>
                <li>Для <a href="https://support.microsoft.com/en-us/help/4023450/surface-surface-battery-and-power">ползунка производительности</a> требуется задать значение "Лучшая производительность" во время использования</li>
            </ul>
        </td>
    </tr>
</table>

## <a name="see-also"></a>См. также раздел
* [Спросить у сообщества](https://answers.microsoft.com)
* [Свяжитесь с нами для получения поддержки](https://support.microsoft.com/contactus/)
* [Рекомендуемые адаптеры для ПК с поддержкой Windows Mixed Reality](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
