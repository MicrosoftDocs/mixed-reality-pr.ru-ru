---
title: Распространение приложений
description: Обзор различных вариантов распространения для различных поддерживаемых платформ и хранилищ публикаций.
author: hferrone
ms.author: v-vtieto
ms.date: 12/9/2020
ms.topic: article
keywords: HoloLens, смешанная реальность, впечатляющие головные телефоны, приложение, uwp, отправка, отправка, фильтры, метаданные, требования к системе, ключевые слова, wack, сертификация, пакет, appx, товары
ms.openlocfilehash: bb4188eaba247730a80c40f669eb498b9d8ef83a
ms.sourcegitcommit: bea83261bf9ce7a27a618e5bc54dc4d7711f5435
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2021
ms.locfileid: "130155572"
---
# <a name="distributing-your-apps"></a>Распространение приложений

![Трехмерное приложение с плавающей высоты ланчер в ВМР Home](images/distribute-hero-image.png)

Получение приложений в руки пользователей или по всему миру является наиболее важным и, порой тщательного, частью любых усилий по разработке. Мы упростили процесс в набор ресурсов, который зависит от сценария распространения и развертывания, который лучше всего подходит вам или вашей команде.

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a>Параметры распределения

> [!IMPORTANT]
> * Если вы используете приложение совместно с другой стороной, необходимо создать файл Appx и предоставить его. 
>     * Если вы используете установщик приложения, вам также потребуется предоставить сертификат пользователю.
> 
> * Если вы используете совместно с Организацией, вам потребуется рабочая или учебная учетная запись и доступ к инфраструктуре [MDM (Управление мобильными устройствами)](/hololens/hololens-enroll-mdm) .  
>    * если вы являетесь субъектом общего доступа, вам нужно быть администратором в клиенте и использовать [центр администрирования Microsoft Endpoint Manager](/mem/intune/apps/apps-deploy) , чтобы сделать приложение доступным. Другим вариантом является совместное использование appx-файла и зависимостей приложения с конечным пользователем.
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
    <td><strong>Установки на локальном устройстве</strong></td>
    <td><strong>Поделиться с кем угодно</strong></td>
    <td><strong>Поделиться с Организацией</strong></td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-app-installer"><strong>Установщик приложения</strong></td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-app-installer"><strong>MDM — Корпоративный портал</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-intune"><strong>Установка приложения, требуемого для MDM</strong></a></td>
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
    <td><a href="/hololens/app-deploy-store-business"><strong>Microsoft Store для бизнеса</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-provisioning-package"><strong>Пакет подготовки</strong></a></td>
    <td>✔️</td>
    <td>✔️</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="#other-scenarios"><strong>пользовательское развертывание Win32</strong></a> (недоступно для устройств HoloLens — см. ниже)</td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> установщик приложения сейчас недоступен для управляемых устройств или HoloLens (1-го поколения) устройств.

## <a name="other-scenarios"></a>Другие сценарии

* Вы можете создать файл .EXE Win32 с помощью автономного целевого объекта сборки на компьютере из Unity для развертывания приложений Win32, включая Steam и Game Pass. Получив .EXE, вы можете отправить свои приложения как обычные на выбранную платформу. 

* если необходимо установить HoloLens 2 приложение в автономном режиме, см. инструкции в [автономном HoloLens 2](/hololens/hololens-common-scenarios-offline-secure) и установите приложение с помощью пакета подготовки без включения режима разработчика.

* вы также можете развернуть сборки на устройстве и предоставить к ним доступ другим разработчикам, использующим режим разработчика, путем [развертывания и отладки с Visual Studio](../develop/advanced-concepts/using-visual-studio.md) или [установки пакета приложения с помощью портала устройств](../develop/advanced-concepts/using-the-windows-device-portal.md#sideloading-applications).

## <a name="see-also"></a>См. также раздел
* [Поиск, установка и удаление приложений из Microsoft Store](/hololens/holographic-store-apps)