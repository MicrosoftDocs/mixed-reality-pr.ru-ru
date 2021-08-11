---
title: Заметки о выпуске — август 2016 г.
description: запишитесь на HoloLens заметок о выпуске Windows 10 годовщина для 2016.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, заметки о выпуске, ос, платформа, функции, коммерческий набор
ms.openlocfilehash: 2cb6153877b27ce0e1260696447bd4c5c851c6f00a20a7889b855c5646e8871f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202469"
---
# <a name="release-notes---august-2016"></a>Заметки о выпуске — август 2016 г.

группа HoloLens прослушивает отзывы разработчиков в программе предварительной оценки Windows, чтобы расставить приоритеты для нашей работы. Продолжайте [предоставлять отзыв](/windows/mixed-reality/give-us-feedback) через центр обратной связи, [форумы для разработчиков](https://forums.hololens.com) и [Twitter с @HoloLens помощью ](https://twitter.com/hololens). по мере того, как Windows 10 приступит к годовщине обновления, группа HoloLens с радостью повышают эффективность работы с holographic. В этом обновлении мы посвящены основным исправлениям, улучшениям и внедрению функций, запрошенных компаниями и доступных в Microsoft HoloLens Commercial Suite.

**последний выпуск:** обновление Windows holographic августа 2016 (**10.0.14393.0**, Windows 10 годовщина)

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

чтобы [обновить текущий выпуск](/windows/mixed-reality/updating-hololens), откройте приложение *Параметры* , перейдите в раздел *обновление & безопасность*, а затем нажмите кнопку *проверить наличие обновлений* .

## <a name="new-features"></a>новые функции;

**присоединение к процессу отладки** HoloLens теперь поддерживает отладку присоединения к процессу. с помощью Visual Studio 2015 с обновлением 3 можно подключиться к работающему приложению на HoloLens и [начать его отладку](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-visual-studio#debugging-an-installed-or-running-app). это работает без необходимости развертывания из проекта Visual Studio.

**обновленные HoloLens Emulator** мы также выпустили обновленную версию HoloLens Emulator.

**Поддержка игровых** устройств теперь вы можете связывать и использовать Bluetooth игровые планшеты с HoloLens! недавно выпущенные беспроводные контроллеры Xbox Bluetooth возможности и могут использоваться для воспроизведения избранных игр и приложений, поддерживающих игровой планшет. Необходимо установить [Обновление контроллера](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) , прежде чем можно будет подключить беспроводной контроллер Xbox к HoloLens. Контроллер беспроводной связи Xbox S поддерживается [ксинпут](/windows/win32/xinput/xinput-game-controller-apis-portal) и [Windows. API-интерфейсы игр. Input](/uwp/api/Windows.Gaming.Input) . можно получить доступ к дополнительным моделям Bluetooth контроллеров с помощью [Windows. API игр. Input](/uwp/api/Windows.Gaming.Input) .

## <a name="improvements-and-fixes"></a>Улучшения и исправления

мы собираемся синхронизироваться с оставшейся частью Windows 10 годовщина, поэтому в дополнение к HoloLensным исправлениям вы также получаете все самое от обновления Windows, чтобы повысить надежность и производительность платформы. Ваши отзывы очень значимы и имеют приоритет для исправлений в выпуске.

Мы улучшили следующие возможности:
* Вход в систему.
* рабочие места присоединяются.
* Энергосбережение для переходов в состояние электропитания устройства.
* стабильность с захватами смешанной реальности.
* надежность подключения к Bluetooth
* сохраняемая голограмма в сценарии с несколькими приложениями.

Мы устранили следующие проблемы:
* сбой подключения профилировщиков Visual Studio и графического отладчика.
* фотографии & документы не отображаются в проводнике на портале устройств.
* Панель приложений может мигать, когда курсор помещается над ним в режиме корректировки.
* В режиме корректировки курсор глаза будет меняться на указатель с 4 стрелками, что приведет к более медленной точке.
* "эй Кортана воспроизвести музыку" не запускается Groove.
* После предыдущего обновления, говорящего на «Go Home», панель «контакты» не отображается правильно.

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Введение в Microsoft HoloLens Commercial Suite

Microsoft HoloLens Commercial Suite готов к развертыванию в масштабе предприятия. Мы добавили несколько очень востребованных [коммерческих функций](/windows/mixed-reality/commercial-features) от наших ранних бизнес-партнеров.

Обратитесь к локальному менеджеру учетная запись Майкрософт, чтобы приобрести Microsoft HoloLens Commercial Suite.

### <a name="key-commercial-features"></a>Основные коммерческие функции 

* **Режим терминала.** с помощью режима киоска HoloLens можно ограничить количество приложений, которые будут запускаться, чтобы включить демонстрацию или показать опыт работы.<br>
  ![в режиме киоска HoloLens запускается непосредственно в выбранном приложении.](images/201608-kioskmode-400px.png)
* **Управление мобильными устройствами (MDM) для HoloLens.** ит-отдел может управлять несколькими HoloLens устройствами одновременно с помощью таких решений, как Microsoft Intune. Вы можете управлять параметрами, выбирать приложения для установки и настройки конфигураций безопасности, соответствующих потребностям вашей организации.<br>
  ![управление мобильными устройствами на HoloLens обеспечивает управление устройствами корпоративного класса на нескольких устройствах.](images/201608-enterprisemanagement-400px.png)
* **Центр обновления Windows для бизнеса.** Контролируемые обновления операционной системы на устройствах и поддержка долгосрочного обслуживания филиала.
* **Защита данных.** На HoloLens включено шифрование данных BitLocker, которое обеспечивает такой же уровень защиты, как на любом устройстве под управлением Windows.
* **Рабочий доступ.** Любой пользователь в Организации может удаленно подключаться к корпоративной сети через виртуальную частную сеть на HoloLens. HoloLens также может подключаться к сетям Wi-Fi, для которых требуются учетные данные.
* **Microsoft Store для бизнеса.** ит-отдел также может настроить корпоративное личное хранилище, содержащее только приложения вашей компании для конкретного HoloLens использования. Это позволяет безопасно распространять корпоративное программное обеспечение среди выбранной группы корпоративных пользователей.

### <a name="development-edition-vs-commercial-suite"></a>Выпуск Development Edition и коммерческий набор

<table>
<tr>
<th>Компоненты</th><th>Выпуск Development Edition</th><th>Коммерческий набор</th>
</tr><tr>
<td>Шифрование устройства (BitLocker)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Виртуальная частная сеть (VPN)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal#kiosk-mode">Полноэкранный режим</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Управление и развертывание</th>
</tr><tr>
<td>Управление мобильными устройствами (MDM)</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Возможность блокировки отмены регистрации</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Корпоративный Wi-Fi доступ на основе сертификатов</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store (потребители)</td><td style="text-align: center;">Потребители</td><td style="text-align: center;">Фильтрация с помощью MDM</td>
</tr><tr>
<td><a href="/microsoft-store/working-with-line-of-business-apps">Портал Store для бизнеса</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Безопасность и идентификация</th>
</tr><tr>
<td>Вход с помощью Azure Active Directory (AAD)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Вход с помощью учетной записи Майкрософт (MSA)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Учетные данные следующего поколения с разблокировкой по PIN-коду</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows-hardware/design/device-experiences/oem-secure-boot">Безопасная загрузка</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Обслуживание и поддержка</th>
</tr><tr>
<td>Автоматическое обновление системы по мере поступления обновлений</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
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