---
title: Распространение приложений
description: Обзор различных вариантов распространения для различных поддерживаемых платформ и хранилищ публикаций.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: HoloLens, Mixed Reality, впечатляющие гарнитуры, приложение, UWP, отправка, отправка, фильтры, метаданные, требования к системе, ключевые слова, wack, сертификация, пакет, appx, товары
ms.openlocfilehash: 5c7a1d6e00610a4046bd71b07ca5184399c9e335
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/09/2020
ms.locfileid: "96925775"
---
# <a name="distributing-your-apps"></a><span data-ttu-id="e02ea-104">Распространение приложений</span><span class="sxs-lookup"><span data-stu-id="e02ea-104">Distributing your apps</span></span>

![Трехмерное приложение с плавающей высоты ланчер в ВМР Home](images/distribute-hero-image.png)

<span data-ttu-id="e02ea-106">Получение приложений в руки пользователей или по всему миру является наиболее важным и, порой тщательного, частью любых усилий по разработке.</span><span class="sxs-lookup"><span data-stu-id="e02ea-106">Getting your apps into the hands of your users or out into the world is the most important, and sometimes painstaking, part of any development effort.</span></span> <span data-ttu-id="e02ea-107">Мы упростили процесс работы с набором перечисленных ниже ресурсов, все из которых зависят от сценария распространения и развертывания, который лучше всего подходит вам или вашей команде.</span><span class="sxs-lookup"><span data-stu-id="e02ea-107">We've simplified process into a set of resources listed below, all of which depend on the distribution and deployment scenario that's best suited for you or your team.</span></span>

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a><span data-ttu-id="e02ea-108">Параметры распределения</span><span class="sxs-lookup"><span data-stu-id="e02ea-108">Distribution options</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="e02ea-109">Если вы используете приложение совместно с другой стороной, необходимо создать файл Appx и предоставить его.</span><span class="sxs-lookup"><span data-stu-id="e02ea-109">If you're sharing your app with another party, you need to build and supply the appx file.</span></span> 
>     * <span data-ttu-id="e02ea-110">Если вы используете установщик приложения, вам также потребуется предоставить сертификат пользователю.</span><span class="sxs-lookup"><span data-stu-id="e02ea-110">If you're using App Installer, you'll also need to share the certificate with the user.</span></span>
> 
> * <span data-ttu-id="e02ea-111">Если вы используете совместно с Организацией, вам потребуется рабочая или учебная учетная запись и доступ к инфраструктуре [MDM (Управление мобильными устройствами)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) .</span><span class="sxs-lookup"><span data-stu-id="e02ea-111">If you're sharing with an organization, you need a work or school account and access to the organizations [MDM (Mobile Device Management)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) infrastructure.</span></span>  
>    * <span data-ttu-id="e02ea-112">Если вы являетесь субъектом общего доступа, необходимо быть администратором клиента и использовать [центр администрирования Microsoft Endpoint Manager](https://docs.microsoft.com/mem/intune/apps/apps-deploy) , чтобы сделать приложение доступным.</span><span class="sxs-lookup"><span data-stu-id="e02ea-112">If you're the sharing party, you need to be an Admin in your tenant and use the [Microsoft Endpoint Manager admin center](https://docs.microsoft.com/mem/intune/apps/apps-deploy) to make the app available.</span></span> <span data-ttu-id="e02ea-113">Другим вариантом является совместное использование appx-файла и зависимостей приложения с конечным пользователем.</span><span class="sxs-lookup"><span data-stu-id="e02ea-113">Another option is to share the appx file and the app dependencies with your end user.</span></span>
>    * <span data-ttu-id="e02ea-114">Если вы являетесь конечным пользователем, приложение будет автоматически скачиваться или быть доступным для скачивания после регистрации в клиенте организации общего доступа.</span><span class="sxs-lookup"><span data-stu-id="e02ea-114">If you're the end user, the app will either automatically download or be available for download once you enroll with the sharing organization's tenant.</span></span> 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><span data-ttu-id="e02ea-115"><strong>Сценарий</strong></span><span class="sxs-lookup"><span data-stu-id="e02ea-115"><strong>Scenario</strong></span></span></td>
    <td><span data-ttu-id="e02ea-116"><strong>Установка локального устройства</strong></span><span class="sxs-lookup"><span data-stu-id="e02ea-116"><strong>Local device install</strong></span></span></td>
    <td><span data-ttu-id="e02ea-117"><strong>Поделиться с кем угодно</strong></span><span class="sxs-lookup"><span data-stu-id="e02ea-117"><strong>Share with anyone</strong></span></span></td>
    <td><span data-ttu-id="e02ea-118"><strong>Поделиться с Организацией</strong></span><span class="sxs-lookup"><span data-stu-id="e02ea-118"><strong>Share with an organization</strong></span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="e02ea-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>Установщик приложения</strong></a> (с помощью <a href="https://docs.microsoft.com/hololens/hololens-insider">сборок программы предварительной оценки Windows</a>)</span><span class="sxs-lookup"><span data-stu-id="e02ea-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>App Installer</strong></a> (through <a href="https://docs.microsoft.com/hololens/hololens-insider">Windows Insider builds</a>)</span></span></td>
    <td><span data-ttu-id="e02ea-120">✔️</span><span class="sxs-lookup"><span data-stu-id="e02ea-120">✔️</span></span></td>
    <td><span data-ttu-id="e02ea-121">✔️</span><span class="sxs-lookup"><span data-stu-id="e02ea-121">✔️</span></span></td>
    <td>❌</td>
</tr>
<tr>
    <td><span data-ttu-id="e02ea-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM — корпоративный портал</strong></a></span><span class="sxs-lookup"><span data-stu-id="e02ea-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM - Company Portal</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="e02ea-123">✔️</span><span class="sxs-lookup"><span data-stu-id="e02ea-123">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="e02ea-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>Установка приложения, требуемого для MDM</strong></a></span><span class="sxs-lookup"><span data-stu-id="e02ea-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM - Required App Install</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="e02ea-125">✔️</span><span class="sxs-lookup"><span data-stu-id="e02ea-125">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="e02ea-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span><span class="sxs-lookup"><span data-stu-id="e02ea-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span></span></td>
    <td>❌</td>
    <td><span data-ttu-id="e02ea-127">✔️</span><span class="sxs-lookup"><span data-stu-id="e02ea-127">✔️</span></span></td>
    <td><span data-ttu-id="e02ea-128">✔️</span><span class="sxs-lookup"><span data-stu-id="e02ea-128">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="e02ea-129"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store для бизнеса</strong></a></span><span class="sxs-lookup"><span data-stu-id="e02ea-129"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store for Business</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="e02ea-130">✔️</span><span class="sxs-lookup"><span data-stu-id="e02ea-130">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="e02ea-131"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Подготовка пакета</strong></a></span><span class="sxs-lookup"><span data-stu-id="e02ea-131"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Provisioning Package</strong></a></span></span></td>
    <td><span data-ttu-id="e02ea-132">✔️</span><span class="sxs-lookup"><span data-stu-id="e02ea-132">✔️</span></span></td>
    <td><span data-ttu-id="e02ea-133">✔️</span><span class="sxs-lookup"><span data-stu-id="e02ea-133">✔️</span></span></td>
    <td><span data-ttu-id="e02ea-134">✔️</span><span class="sxs-lookup"><span data-stu-id="e02ea-134">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="e02ea-135"><a href="#additional-scenarios"><strong>Пользовательское развертывание Win32</strong></a> (недоступно для устройств HoloLens — см. ниже)</span><span class="sxs-lookup"><span data-stu-id="e02ea-135"><a href="#additional-scenarios"><strong>Custom Win32 deployment</strong></a> (Not available for HoloLens devices - see below)</span></span></td>
    <td><span data-ttu-id="e02ea-136">✔️</span><span class="sxs-lookup"><span data-stu-id="e02ea-136">✔️</span></span></td>
    <td><span data-ttu-id="e02ea-137">✔️</span><span class="sxs-lookup"><span data-stu-id="e02ea-137">✔️</span></span></td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> <span data-ttu-id="e02ea-138">Установщик приложения сейчас недоступен для управляемых устройств или устройств HoloLens (1-го поколения).</span><span class="sxs-lookup"><span data-stu-id="e02ea-138">App Installer isn't currently available for managed devices or HoloLens (1st Gen) devices.</span></span>

## <a name="additional-scenarios"></a><span data-ttu-id="e02ea-139">Дополнительные сценарии</span><span class="sxs-lookup"><span data-stu-id="e02ea-139">Additional scenarios</span></span>

* <span data-ttu-id="e02ea-140">Для развертывания приложений Win32, включая Steam и Pass, можно создать Win32. EXE, используя целевой объект автономной сборки ПК из Unity и отправляйте свои приложения как обычные для выбранной платформы.</span><span class="sxs-lookup"><span data-stu-id="e02ea-140">For Win32 application deployment, including Steam and Game Pass, you can produce a Win32 .EXE file using the PC Standalone build target from Unity and submit your apps as normal to your chosen platform.</span></span> 

* <span data-ttu-id="e02ea-141">Если вы хотите установить приложение HoloLens 2 в автономном режиме, обратитесь к инструкциям в [автономном режиме безопасности HoloLens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) или установите приложение с помощью пакета подготовки без включения режима разработчика.</span><span class="sxs-lookup"><span data-stu-id="e02ea-141">If you need to install a HoloLens 2 application while you're offline, refer to the [offline secure HoloLens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) instructions or instal the app through a Provisioning Package without enabling developer mode.</span></span>

* <span data-ttu-id="e02ea-142">Вы также можете развернуть сборки на устройстве и предоставить к ним доступ другим разработчикам, использующим режим разработчика, путем [развертывания и отладки в Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) или [установки пакета приложения с помощью портала устройств](https://docs.microsoft.com/hololens/holographic-custom-apps#installing-an-application-package-with-the-device-portal).</span><span class="sxs-lookup"><span data-stu-id="e02ea-142">You can also deploy builds to your device and share them with other developers who have Developer Mode enabled by [deploying and debugging with Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) or [installing an application package with the Device Portal](https://docs.microsoft.com/hololens/holographic-custom-apps#installing-an-application-package-with-the-device-portal).</span></span>

## <a name="see-also"></a><span data-ttu-id="e02ea-143">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="e02ea-143">See also</span></span>
* [<span data-ttu-id="e02ea-144">Поиск, установка и удаление приложений из Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="e02ea-144">Finding, installing, and uninstalling applications from the Microsoft Store</span></span>](https://docs.microsoft.com/hololens/holographic-store-apps)

<!-- ## Submitting to the Microsoft Store

You've finally made it to the last step on your distribution journey, actually getting your app into the Microsoft Store! Our [submission guidelines](submitting-an-app-to-the-microsoft-store.md) article will take you through: 

* Partner Center registration 
* Asset preparation
* App packaging
* Testing
* Final submission process

You can even give out free trials to get future consumers excited about your new immersive experience. Once your app is listed on the Microsoft Store you can sit back, engage with your expanding user community, and think about all the new features you want to add! -->
