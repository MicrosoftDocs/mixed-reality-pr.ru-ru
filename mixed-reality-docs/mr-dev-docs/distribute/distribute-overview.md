---
title: Распространение приложений
description: Обзор различных вариантов распространения для различных поддерживаемых платформ и хранилищ публикаций.
author: hferrone
ms.author: v-hferrone
ms.date: 10/02/2020
ms.topic: article
keywords: HoloLens, Mixed Reality, впечатляющие гарнитуры, приложение, UWP, отправка, отправка, фильтры, метаданные, требования к системе, ключевые слова, wack, сертификация, пакет, appx, товары
ms.openlocfilehash: 4ea60d2111f99924eaa417d4ff6fa8830934588c
ms.sourcegitcommit: 9c640c96e2270ef69edd46f1b12acb00b373554d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2020
ms.locfileid: "96578883"
---
# <a name="distributing-your-apps"></a>Распространение приложений

![Трехмерное приложение с плавающей высоты ланчер в ВМР Home](images/distribute-hero-image.png)

Получение приложений в руки пользователей или по всему миру является наиболее важным и, порой тщательного, частью любых усилий по разработке. Мы упростили процесс работы с набором перечисленных ниже ресурсов, все из которых зависят от сценария распространения и развертывания, который лучше всего подходит вам или вашей команде.

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a>Параметры распределения

> [!IMPORTANT]
> * Если вы используете приложение совместно с другой стороной, необходимо создать файл Appx и предоставить его. 
>     * Если вы используете установщик приложения, вам также потребуется предоставить сертификат пользователю.
> 
> * Если вы используете совместно с Организацией, вам потребуется рабочая или учебная учетная запись и доступ к инфраструктуре [MDM (Управление мобильными устройствами)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) .  
>    * Если вы являетесь субъектом общего доступа, необходимо быть администратором клиента и использовать [центр администрирования Microsoft Endpoint Manager](https://docs.microsoft.com/mem/intune/apps/apps-deploy) , чтобы сделать приложение доступным. Другим вариантом является совместное использование appx-файла и зависимостей приложения с конечным пользователем.
>    * Если вы являетесь конечным пользователем, приложение будет автоматически скачиваться или быть доступным для скачивания после регистрации в клиенте организации общего доступа. 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><strong>Сценарий</strong></td>
    <td><strong>Установка локального устройства</strong></td>
    <td><strong>Поделиться с кем угодно</strong></td>
    <td><strong>Поделиться с Организацией</strong></td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>Установщик приложения</strong></a> (с помощью <a href="https://docs.microsoft.com/hololens/hololens-insider">сборок программы предварительной оценки Windows</a>)</td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM — корпоративный портал</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>Установка приложения, требуемого для MDM</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></td>
    <td>❌</td>
    <td>✔️</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store для бизнеса</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Подготовка пакета</strong></a></td>
    <td>✔️</td>
    <td>✔️</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="#additional-scenarios"><strong>Пользовательское развертывание Win32</strong></a> (недоступно для устройств HoloLens — см. ниже)</td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> Установщик приложения сейчас недоступен для управляемых устройств или устройств HoloLens (1-го поколения).

## <a name="additional-scenarios"></a>Дополнительные сценарии

* Для развертывания приложений Win32, включая Steam и Pass, можно создать Win32. EXE, используя целевой объект автономной сборки ПК из Unity и отправляйте свои приложения как обычные для выбранной платформы. 

* Если вы хотите установить приложение HoloLens 2 в автономном режиме, обратитесь к инструкциям в [автономном режиме безопасности HoloLens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) или установите приложение с помощью пакета подготовки без включения режима разработчика.

* Вы также можете развернуть сборки на устройстве и предоставить к ним доступ другим разработчикам, использующим режим разработчика, путем [развертывания и отладки в Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) или [установки пакета приложения с помощью портала устройств](https://docs.microsoft.com/hololens/holographic-custom-apps#installing-an-application-package-with-the-device-portal).

## <a name="see-also"></a>См. также
* [Поиск, установка и удаление приложений из Microsoft Store](https://docs.microsoft.com/hololens/holographic-store-apps)

<!-- ## Submitting to the Microsoft Store

You've finally made it to the last step on your distribution journey, actually getting your app into the Microsoft Store! Our [submission guidelines](submitting-an-app-to-the-microsoft-store.md) article will take you through: 

* Partner Center registration 
* Asset preparation
* App packaging
* Testing
* Final submission process

You can even give out free trials to get future consumers excited about your new immersive experience. Once your app is listed on the Microsoft Store you can sit back, engage with your expanding user community, and think about all the new features you want to add! -->
