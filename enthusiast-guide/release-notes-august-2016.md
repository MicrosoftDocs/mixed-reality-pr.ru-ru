---
title: Заметки о выпуске — август 2016 г.
description: Оставайтесь в курсе заметок о выпуске HoloLens для годовщины Windows 10 на 2016.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, заметки о выпуске, ОС, платформа, функции, коммерческий набор
ms.openlocfilehash: c70da10043cfbcfa88105635f2467c8feaadbedf
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581648"
---
# <a name="release-notes---august-2016"></a>Заметки о выпуске — август 2016 г.

Команда HoloLens прослушивает Отзывы разработчиков в программе предварительной оценки Windows, чтобы задать приоритеты для нашей работы. Продолжайте [предоставлять отзыв](/windows/mixed-reality/give-us-feedback) через центр обратной связи, [форумы для разработчиков](https://forums.hololens.com) и [Twitter с @HoloLens помощью ](https://twitter.com/hololens). Так как в Windows 10 включено годовщина, Группа HoloLens с радостью попытается улучшить работу с Holographic. В этом обновлении мы посвящены основным исправлениям, улучшениям и внедрению функций, запрошенных компаниями и доступных в коммерческом наборе Microsoft HoloLens.

**Последний выпуск:** Обновление Windows holographic 2016 августа (**10.0.14393.0**, Юбилейная версия Windows 10)

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

Чтобы [обновить текущий выпуск](/windows/mixed-reality/updating-hololens), откройте приложение " *Параметры* ", перейдите в раздел " *Обновление & безопасность*", а затем нажмите кнопку " *проверить обновления* ".

## <a name="new-features"></a>новые функции;

**Присоединение к процессу отладки** HoloLens теперь поддерживает отладку присоединения к процессу. Вы можете использовать обновление 3 для Visual Studio 2015, чтобы подключиться к работающему приложению на HoloLens и [начать его отладку](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-visual-studio#debugging-an-installed-or-running-app). Это работает без необходимости развертывания из проекта Visual Studio.

**Обновленный эмулятор HoloLens** Мы также выпустили обновленную версию эмулятора HoloLens.

**Поддержка игровых** устройств Теперь вы можете связывать и использовать игровые устройства Bluetooth с HoloLens! Недавно выпущенный адаптер Xbox Wireless поддерживает функции Bluetooth и может использоваться для воспроизведения избранных игр и приложений, поддерживающих игровой планшет. Перед подключением контроллера беспроводной сети Xbox к серверу HoloLens необходимо применить [Обновление контроллера](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) . Контроллер беспроводной связи Xbox S поддерживается интерфейсами API [ксинпут](/windows/win32/xinput/xinput-game-controller-apis-portal) и [Windows. Gaming. input.](/uwp/api/Windows.Gaming.Input) Доступ к нескольким моделям контроллеров Bluetooth можно получить с помощью API [Windows. Gaming. Input](/uwp/api/Windows.Gaming.Input) .

## <a name="improvements-and-fixes"></a>Улучшения и исправления

Мы работаем над обновлением годовщины Windows 10, поэтому в дополнение к исправлениям для HoloLens вы получаете также все самое самое от центра обновления Windows, чтобы повысить надежность и производительность платформы. Ваши отзывы очень значимы и имеют приоритет для исправлений в выпуске.

Мы улучшили следующие возможности:
* Вход в систему.
* рабочие места присоединяются.
* Энергосбережение для переходов в состояние электропитания устройства.
* стабильность с захватами смешанной реальности.
* надежность подключения Bluetooth
* сохраняемая голограмма в сценарии с несколькими приложениями.

Мы устранили следующие проблемы:
* не удается подключиться к профилировщику и отладчику графики Visual Studio.
* фотографии & документы не отображаются в проводнике на портале устройств.
* Панель приложений может мигать, когда курсор помещается над ним в режиме корректировки.
* В режиме корректировки курсор глаза будет меняться на указатель с 4 стрелками, что приведет к более медленной точке.
* "Привет, Кортана, воспроизведение музыки" не запускает Groove.
* После предыдущего обновления, говорящего на «Go Home», панель «контакты» не отображается правильно.

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Знакомство с коммерческим набором Microsoft HoloLens

Коммерческий набор Microsoft HoloLens готов для корпоративного развертывания. Мы добавили несколько очень востребованных [коммерческих функций](/windows/mixed-reality/commercial-features) от наших ранних бизнес-партнеров.

Обратитесь к локальному менеджеру учетная запись Майкрософт, чтобы приобрести коммерческий набор Microsoft HoloLens.

### <a name="key-commercial-features"></a>Основные коммерческие функции 

* **Режим киоска.** С помощью режима киоска HoloLens можно ограничить количество приложений, которые будут запускаться, чтобы включить демонстрационные или демонстрационные возможности.<br>
  ![В режиме киоска HoloLens запускается непосредственно в выбранном приложении.](images/201608-kioskmode-400px.png)
* **Управление мобильными устройствами (MDM) для HoloLens.** ИТ-отдел может управлять несколькими устройствами HoloLens одновременно, используя такие решения, как Microsoft Intune. Вы можете управлять параметрами, выбирать приложения для установки и настройки конфигураций безопасности, соответствующих потребностям вашей организации.<br>
  ![Управление мобильными устройствами в HoloLens обеспечивает управление устройствами корпоративного класса на нескольких устройствах.](images/201608-enterprisemanagement-400px.png)
* **Центр обновления Windows для бизнеса.** Контролируемые обновления операционной системы на устройствах и поддержка долгосрочного обслуживания филиала.
* **Безопасность данных.** Шифрование данных BitLocker включено в HoloLens для обеспечения того же уровня защиты безопасности, что и любое другое устройство Windows.
* **Рабочий доступ.** Любой пользователь в Организации может удаленно подключаться к корпоративной сети через виртуальную частную сеть на HoloLens. HoloLens также может получать доступ к Wi-Fi сетям, которым требуются учетные данные.
* **Microsoft Store для бизнеса.** ИТ-отдел также может настроить корпоративное личное хранилище, содержащее только приложения вашей компании для конкретного использования HoloLens. Безопасное распространение корпоративного программного обеспечения в выбранную группу корпоративных пользователей.

### <a name="development-edition-vs-commercial-suite"></a>Выпуск Development Edition и коммерческий набор

<table>
<tr>
<th>Компоненты</th><th>Выпуск Development Edition</th><th>Коммерческий набор</th>
</tr><tr>
<td>Шифрование устройства (BitLocker)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Виртуальная частная сеть (VPN)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal#kiosk-mode">Режим киоска</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Управление и развертывание</th>
</tr><tr>
<td>Управление мобильными устройствами (MDM)</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Возможность блокировать отмену регистрации</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Корпоративный Wi-Fi доступ на основе сертификатов</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store (потребитель)</td><td style="text-align: center;">Потребители</td><td style="text-align: center;">Фильтрация с помощью MDM</td>
</tr><tr>
<td><a href="/microsoft-store/working-with-line-of-business-apps">Портал бизнес-магазина</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Безопасность и удостоверения</th>
</tr><tr>
<td>Вход с помощью Azure Active Directory (AAD)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Вход с помощью учетной записи Майкрософт (MSA)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Учетные данные следующего поколения с разблокированием ПИН-кода</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows-hardware/design/device-experiences/oem-secure-boot">Безопасная загрузка</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Обслуживание и поддержка</th>
</tr><tr>
<td>Автоматические обновления системы по мере их поступления</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows/deployment/update/waas-manage-updates-wufb">Центр обновления Windows для бизнеса.</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Long Term Servicing Branch</td><td></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="prior-release-notes"></a>Заметки о предыдущем выпуске
* [Заметки о выпуске — май 2016 г.](release-notes-may-2016.md)
* [Заметки о выпуске — март 2016 г.](release-notes-march-2016.md)

## <a name="see-also"></a>См. также раздел
* [Известные проблемы с HoloLens](/windows/mixed-reality/hololens-known-issues)
* [Коммерческие функции](/windows/mixed-reality/commercial-features)
* [Установка средств](/windows/mixed-reality/develop/install-the-tools)
* [Использование эмулятора HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)