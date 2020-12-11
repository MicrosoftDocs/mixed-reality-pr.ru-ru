---
title: Распространение приложений
description: Обзор различных вариантов распространения для различных поддерживаемых платформ и хранилищ публикаций.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: HoloLens, Mixed Reality, впечатляющие гарнитуры, приложение, UWP, отправка, отправка, фильтры, метаданные, требования к системе, ключевые слова, wack, сертификация, пакет, appx, товары
ms.openlocfilehash: b4b82557ba274852ebb3f97058017fa2e5db1c02
ms.sourcegitcommit: 9e9d58de4513655c7daa71ff4b5b2c2b115ab959
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "97034585"
---
# <a name="distributing-your-apps"></a><span data-ttu-id="2f313-104">Распространение приложений</span><span class="sxs-lookup"><span data-stu-id="2f313-104">Distributing your apps</span></span>

![Трехмерное приложение с плавающей высоты ланчер в ВМР Home](images/distribute-hero-image.png)

<span data-ttu-id="2f313-106">Получение приложений в руки пользователей или по всему миру является наиболее важным и, порой тщательного, частью любых усилий по разработке.</span><span class="sxs-lookup"><span data-stu-id="2f313-106">Getting your apps into the hands of your users or out into the world is the most important, and sometimes painstaking, part of any development effort.</span></span> <span data-ttu-id="2f313-107">Мы упростили процесс работы с набором перечисленных ниже ресурсов, все из которых зависят от сценария распространения и развертывания, который лучше всего подходит вам или вашей команде.</span><span class="sxs-lookup"><span data-stu-id="2f313-107">We've simplified process into a set of resources listed below, all of which depend on the distribution and deployment scenario that's best suited for you or your team.</span></span>

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a><span data-ttu-id="2f313-108">Параметры распределения</span><span class="sxs-lookup"><span data-stu-id="2f313-108">Distribution options</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="2f313-109">Если вы используете приложение совместно с другой стороной, необходимо создать файл Appx и предоставить его.</span><span class="sxs-lookup"><span data-stu-id="2f313-109">If you're sharing your app with another party, you need to build and supply the appx file.</span></span> 
>     * <span data-ttu-id="2f313-110">Если вы используете установщик приложения, вам также потребуется предоставить сертификат пользователю.</span><span class="sxs-lookup"><span data-stu-id="2f313-110">If you're using App Installer, you'll also need to share the certificate with the user.</span></span>
> 
> * <span data-ttu-id="2f313-111">Если вы используете совместно с Организацией, вам потребуется рабочая или учебная учетная запись и доступ к инфраструктуре [MDM (Управление мобильными устройствами)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) .</span><span class="sxs-lookup"><span data-stu-id="2f313-111">If you're sharing with an organization, you need a work or school account and access to the organizations [MDM (Mobile Device Management)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) infrastructure.</span></span>  
>    * <span data-ttu-id="2f313-112">Если вы являетесь субъектом общего доступа, необходимо быть администратором клиента и использовать [центр администрирования Microsoft Endpoint Manager](https://docs.microsoft.com/mem/intune/apps/apps-deploy) , чтобы сделать приложение доступным.</span><span class="sxs-lookup"><span data-stu-id="2f313-112">If you're the sharing party, you need to be an Admin in your tenant and use the [Microsoft Endpoint Manager admin center](https://docs.microsoft.com/mem/intune/apps/apps-deploy) to make the app available.</span></span> <span data-ttu-id="2f313-113">Другим вариантом является совместное использование appx-файла и зависимостей приложения с конечным пользователем.</span><span class="sxs-lookup"><span data-stu-id="2f313-113">Another option is to share the appx file and the app dependencies with your end user.</span></span>
>    * <span data-ttu-id="2f313-114">Если вы являетесь конечным пользователем, приложение будет автоматически скачиваться или быть доступным для скачивания после регистрации в клиенте организации общего доступа.</span><span class="sxs-lookup"><span data-stu-id="2f313-114">If you're the end user, the app will either automatically download or be available for download once you enroll with the sharing organization's tenant.</span></span> 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><span data-ttu-id="2f313-115"><strong>Сценарий</strong></span><span class="sxs-lookup"><span data-stu-id="2f313-115"><strong>Scenario</strong></span></span></td>
    <td><span data-ttu-id="2f313-116"><strong>Установка локального устройства</strong></span><span class="sxs-lookup"><span data-stu-id="2f313-116"><strong>Local device install</strong></span></span></td>
    <td><span data-ttu-id="2f313-117"><strong>Поделиться с кем угодно</strong></span><span class="sxs-lookup"><span data-stu-id="2f313-117"><strong>Share with anyone</strong></span></span></td>
    <td><span data-ttu-id="2f313-118"><strong>Поделиться с Организацией</strong></span><span class="sxs-lookup"><span data-stu-id="2f313-118"><strong>Share with an organization</strong></span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="2f313-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>Установщик приложения</strong></span><span class="sxs-lookup"><span data-stu-id="2f313-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>App Installer</strong></span></span></td>
    <td><span data-ttu-id="2f313-120">✔️</span><span class="sxs-lookup"><span data-stu-id="2f313-120">✔️</span></span></td>
    <td><span data-ttu-id="2f313-121">✔️</span><span class="sxs-lookup"><span data-stu-id="2f313-121">✔️</span></span></td>
    <td>❌</td>
</tr>
<tr>
    <td><span data-ttu-id="2f313-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM — корпоративный портал</strong></a></span><span class="sxs-lookup"><span data-stu-id="2f313-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM - Company Portal</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="2f313-123">✔️</span><span class="sxs-lookup"><span data-stu-id="2f313-123">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="2f313-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>Установка приложения, требуемого для MDM</strong></a></span><span class="sxs-lookup"><span data-stu-id="2f313-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM - Required App Install</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="2f313-125">✔️</span><span class="sxs-lookup"><span data-stu-id="2f313-125">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="2f313-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span><span class="sxs-lookup"><span data-stu-id="2f313-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span></span></td>
    <td>❌</td>
    <td><span data-ttu-id="2f313-127">✔️</span><span class="sxs-lookup"><span data-stu-id="2f313-127">✔️</span></span></td>
    <td><span data-ttu-id="2f313-128">✔️</span><span class="sxs-lookup"><span data-stu-id="2f313-128">✔️</span></span></td><span data-ttu-id="2f313-129">s</span><span class="sxs-lookup"><span data-stu-id="2f313-129">s</span></span>
</tr>
<tr>
    <td><span data-ttu-id="2f313-130"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store для бизнеса</strong></a></span><span class="sxs-lookup"><span data-stu-id="2f313-130"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store for Business</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="2f313-131">✔️</span><span class="sxs-lookup"><span data-stu-id="2f313-131">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="2f313-132"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Подготовка пакета</strong></a></span><span class="sxs-lookup"><span data-stu-id="2f313-132"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Provisioning Package</strong></a></span></span></td>
    <td><span data-ttu-id="2f313-133">✔️</span><span class="sxs-lookup"><span data-stu-id="2f313-133">✔️</span></span></td>
    <td><span data-ttu-id="2f313-134">✔️</span><span class="sxs-lookup"><span data-stu-id="2f313-134">✔️</span></span></td>
    <td><span data-ttu-id="2f313-135">✔️</span><span class="sxs-lookup"><span data-stu-id="2f313-135">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="2f313-136"><a href="#additional-scenarios"><strong>Пользовательское развертывание Win32</strong></a> (недоступно для устройств HoloLens — см. ниже)</span><span class="sxs-lookup"><span data-stu-id="2f313-136"><a href="#additional-scenarios"><strong>Custom Win32 deployment</strong></a> (Not available for HoloLens devices - see below)</span></span></td>
    <td><span data-ttu-id="2f313-137">✔️</span><span class="sxs-lookup"><span data-stu-id="2f313-137">✔️</span></span></td>
    <td><span data-ttu-id="2f313-138">✔️</span><span class="sxs-lookup"><span data-stu-id="2f313-138">✔️</span></span></td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> <span data-ttu-id="2f313-139">Установщик приложения сейчас недоступен для управляемых устройств или устройств HoloLens (1-го поколения).</span><span class="sxs-lookup"><span data-stu-id="2f313-139">App Installer isn't currently available for managed devices or HoloLens (1st Gen) devices.</span></span>

## <a name="additional-scenarios"></a><span data-ttu-id="2f313-140">Дополнительные сценарии</span><span class="sxs-lookup"><span data-stu-id="2f313-140">Additional scenarios</span></span>

* <span data-ttu-id="2f313-141">Для развертывания приложений Win32, включая Steam и Pass, можно создать Win32. EXE, используя целевой объект автономной сборки ПК из Unity и отправляйте свои приложения как обычные для выбранной платформы.</span><span class="sxs-lookup"><span data-stu-id="2f313-141">For Win32 application deployment, including Steam and Game Pass, you can produce a Win32 .EXE file using the PC Standalone build target from Unity and submit your apps as normal to your chosen platform.</span></span> 

* <span data-ttu-id="2f313-142">Если вы хотите установить приложение HoloLens 2 в автономном режиме, обратитесь к инструкциям в [автономном режиме безопасности HoloLens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) или установите приложение с помощью пакета подготовки без включения режима разработчика.</span><span class="sxs-lookup"><span data-stu-id="2f313-142">If you need to install a HoloLens 2 application while you're offline, refer to the [offline secure HoloLens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) instructions or instal the app through a Provisioning Package without enabling developer mode.</span></span>

* <span data-ttu-id="2f313-143">Вы также можете развернуть сборки на устройстве и предоставить к ним доступ другим разработчикам, использующим режим разработчика, путем [развертывания и отладки в Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) или [установки пакета приложения с помощью портала устройств](https://docs.microsoft.com/hololens/holographic-custom-apps#installing-an-application-package-with-the-device-portal).</span><span class="sxs-lookup"><span data-stu-id="2f313-143">You can also deploy builds to your device and share them with other developers who have Developer Mode enabled by [deploying and debugging with Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) or [installing an application package with the Device Portal](https://docs.microsoft.com/hololens/holographic-custom-apps#installing-an-application-package-with-the-device-portal).</span></span>

## <a name="see-also"></a><span data-ttu-id="2f313-144">См. также</span><span class="sxs-lookup"><span data-stu-id="2f313-144">See also</span></span>
* [<span data-ttu-id="2f313-145">Поиск, установка и удаление приложений из Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="2f313-145">Finding, installing, and uninstalling applications from the Microsoft Store</span></span>](https://docs.microsoft.com/hololens/holographic-store-apps)

