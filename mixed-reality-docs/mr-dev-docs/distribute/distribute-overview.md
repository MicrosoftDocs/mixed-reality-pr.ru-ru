---
title: Распространение приложений
description: Обзор различных вариантов распространения для различных поддерживаемых платформ и хранилищ публикаций.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: HoloLens, Mixed Reality, впечатляющие гарнитуры, приложение, UWP, отправка, отправка, фильтры, метаданные, требования к системе, ключевые слова, wack, сертификация, пакет, appx, товары
ms.openlocfilehash: eb06ff46be6fbe6e480f9b43fa7f23ee47982192
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582849"
---
# <a name="distributing-your-apps"></a><span data-ttu-id="c66f3-104">Распространение приложений</span><span class="sxs-lookup"><span data-stu-id="c66f3-104">Distributing your apps</span></span>

![Трехмерное приложение с плавающей высоты ланчер в ВМР Home](images/distribute-hero-image.png)

<span data-ttu-id="c66f3-106">Получение приложений в руки пользователей или по всему миру является наиболее важным и, порой тщательного, частью любых усилий по разработке.</span><span class="sxs-lookup"><span data-stu-id="c66f3-106">Getting your apps into the hands of your users or out into the world is the most important, and sometimes painstaking, part of any development effort.</span></span> <span data-ttu-id="c66f3-107">Мы упростили процесс в набор ресурсов, который зависит от сценария распространения и развертывания, который лучше всего подходит вам или вашей команде.</span><span class="sxs-lookup"><span data-stu-id="c66f3-107">We've simplified the process into a set of resources, which depend on the distribution and deployment scenario that's best suited for you or your team.</span></span>

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a><span data-ttu-id="c66f3-108">Параметры распределения</span><span class="sxs-lookup"><span data-stu-id="c66f3-108">Distribution options</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="c66f3-109">Если вы используете приложение совместно с другой стороной, необходимо создать файл Appx и предоставить его.</span><span class="sxs-lookup"><span data-stu-id="c66f3-109">If you're sharing your app with another party, you need to build and supply the appx file.</span></span> 
>     * <span data-ttu-id="c66f3-110">Если вы используете установщик приложения, вам также потребуется предоставить сертификат пользователю.</span><span class="sxs-lookup"><span data-stu-id="c66f3-110">If you're using App Installer, you'll also need to share the certificate with the user.</span></span>
> 
> * <span data-ttu-id="c66f3-111">Если вы используете совместно с Организацией, вам потребуется рабочая или учебная учетная запись и доступ к инфраструктуре [MDM (Управление мобильными устройствами)](/hololens/hololens-enroll-mdm) .</span><span class="sxs-lookup"><span data-stu-id="c66f3-111">If you're sharing with an organization, you need a work or school account and access to the organizations [MDM (Mobile Device Management)](/hololens/hololens-enroll-mdm) infrastructure.</span></span>  
>    * <span data-ttu-id="c66f3-112">Если вы являетесь субъектом общего доступа, необходимо быть администратором клиента и использовать [центр администрирования Microsoft Endpoint Manager](/mem/intune/apps/apps-deploy) , чтобы сделать приложение доступным.</span><span class="sxs-lookup"><span data-stu-id="c66f3-112">If you're the sharing party, you need to be an Admin in your tenant and use the [Microsoft Endpoint Manager admin center](/mem/intune/apps/apps-deploy) to make the app available.</span></span> <span data-ttu-id="c66f3-113">Другим вариантом является совместное использование appx-файла и зависимостей приложения с конечным пользователем.</span><span class="sxs-lookup"><span data-stu-id="c66f3-113">Another option is to share the appx file and the app dependencies with your end user.</span></span>
>    * <span data-ttu-id="c66f3-114">Если вы являетесь конечным пользователем, приложение будет автоматически скачиваться или быть доступным для скачивания после регистрации в клиенте организации общего доступа.</span><span class="sxs-lookup"><span data-stu-id="c66f3-114">If you're the end user, the app will either automatically download or be available for download once you enroll with the sharing organization's tenant.</span></span> 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><span data-ttu-id="c66f3-115"><strong>Сценарий</strong></span><span class="sxs-lookup"><span data-stu-id="c66f3-115"><strong>Scenario</strong></span></span></td>
    <td><span data-ttu-id="c66f3-116"><strong>Установки на локальном устройстве</strong></span><span class="sxs-lookup"><span data-stu-id="c66f3-116"><strong>Local device installs</strong></span></span></td>
    <td><span data-ttu-id="c66f3-117"><strong>Поделиться с кем угодно</strong></span><span class="sxs-lookup"><span data-stu-id="c66f3-117"><strong>Share with anyone</strong></span></span></td>
    <td><span data-ttu-id="c66f3-118"><strong>Поделиться с Организацией</strong></span><span class="sxs-lookup"><span data-stu-id="c66f3-118"><strong>Share with an organization</strong></span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="c66f3-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>Установщик приложения</strong></span><span class="sxs-lookup"><span data-stu-id="c66f3-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>App Installer</strong></span></span></td>
    <td><span data-ttu-id="c66f3-120">✔️</span><span class="sxs-lookup"><span data-stu-id="c66f3-120">✔️</span></span></td>
    <td><span data-ttu-id="c66f3-121">✔️</span><span class="sxs-lookup"><span data-stu-id="c66f3-121">✔️</span></span></td>
    <td>❌</td>
</tr>
<tr>
    <td><span data-ttu-id="c66f3-122"><a href="/hololens/app-deploy-app-installer"><strong>MDM — корпоративный портал</strong></a></span><span class="sxs-lookup"><span data-stu-id="c66f3-122"><a href="/hololens/app-deploy-app-installer"><strong>MDM - Company Portal</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="c66f3-123">✔️</span><span class="sxs-lookup"><span data-stu-id="c66f3-123">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="c66f3-124"><a href="/hololens/app-deploy-intune"><strong>Установка приложения, требуемого для MDM</strong></a></span><span class="sxs-lookup"><span data-stu-id="c66f3-124"><a href="/hololens/app-deploy-intune"><strong>MDM - Required App Install</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="c66f3-125">✔️</span><span class="sxs-lookup"><span data-stu-id="c66f3-125">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="c66f3-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span><span class="sxs-lookup"><span data-stu-id="c66f3-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span></span></td>
    <td>❌</td>
    <td><span data-ttu-id="c66f3-127">✔️</span><span class="sxs-lookup"><span data-stu-id="c66f3-127">✔️</span></span></td>
    <td><span data-ttu-id="c66f3-128">✔️</span><span class="sxs-lookup"><span data-stu-id="c66f3-128">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="c66f3-129"><a href="/hololens/app-deploy-store-business"><strong>Microsoft Store для бизнеса</strong></a></span><span class="sxs-lookup"><span data-stu-id="c66f3-129"><a href="/hololens/app-deploy-store-business"><strong>Microsoft Store for Business</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="c66f3-130">✔️</span><span class="sxs-lookup"><span data-stu-id="c66f3-130">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="c66f3-131"><a href="/hololens/app-deploy-provisioning-package"><strong>Подготовка пакета</strong></a></span><span class="sxs-lookup"><span data-stu-id="c66f3-131"><a href="/hololens/app-deploy-provisioning-package"><strong>Provisioning Package</strong></a></span></span></td>
    <td><span data-ttu-id="c66f3-132">✔️</span><span class="sxs-lookup"><span data-stu-id="c66f3-132">✔️</span></span></td>
    <td><span data-ttu-id="c66f3-133">✔️</span><span class="sxs-lookup"><span data-stu-id="c66f3-133">✔️</span></span></td>
    <td><span data-ttu-id="c66f3-134">✔️</span><span class="sxs-lookup"><span data-stu-id="c66f3-134">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="c66f3-135"><a href="#other-scenarios"><strong>Пользовательское развертывание Win32</strong></a> (недоступно для устройств HoloLens — см. ниже)</span><span class="sxs-lookup"><span data-stu-id="c66f3-135"><a href="#other-scenarios"><strong>Custom Win32 deployment</strong></a> (Not available for HoloLens devices - see below)</span></span></td>
    <td><span data-ttu-id="c66f3-136">✔️</span><span class="sxs-lookup"><span data-stu-id="c66f3-136">✔️</span></span></td>
    <td><span data-ttu-id="c66f3-137">✔️</span><span class="sxs-lookup"><span data-stu-id="c66f3-137">✔️</span></span></td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> <span data-ttu-id="c66f3-138">Установщик приложения сейчас недоступен для управляемых устройств или устройств HoloLens (1-го поколения).</span><span class="sxs-lookup"><span data-stu-id="c66f3-138">App Installer isn't currently available for managed devices or HoloLens (1st Gen) devices.</span></span>

## <a name="other-scenarios"></a><span data-ttu-id="c66f3-139">Другие сценарии</span><span class="sxs-lookup"><span data-stu-id="c66f3-139">Other scenarios</span></span>

* <span data-ttu-id="c66f3-140">Вы можете создать Win32. EXE, используя целевой объект автономной сборки ПК из Unity для развертывания приложений Win32, включая Steam и Pass.</span><span class="sxs-lookup"><span data-stu-id="c66f3-140">You can produce a Win32 .EXE file using the PC Standalone build target from Unity for Win32 application deployment, including Steam and Game Pass.</span></span> <span data-ttu-id="c66f3-141">После получения. EXE, вы можете отправить свои приложения обычным образом на выбранную платформу.</span><span class="sxs-lookup"><span data-stu-id="c66f3-141">Once you have the .EXE, you can submit your apps as normal to your chosen platform.</span></span> 

* <span data-ttu-id="c66f3-142">Если вы хотите установить приложение HoloLens 2 в автономном режиме, обратитесь к инструкциям в [автономном режиме безопасности HoloLens 2](/hololens/hololens-common-scenarios-offline-secure) или установите приложение с помощью пакета подготовки без включения режима разработчика.</span><span class="sxs-lookup"><span data-stu-id="c66f3-142">If you need to install a HoloLens 2 application while you're offline, refer to the [offline secure HoloLens 2](/hololens/hololens-common-scenarios-offline-secure) instructions or install the app through a Provisioning Package without enabling developer mode.</span></span>

* <span data-ttu-id="c66f3-143">Вы также можете развернуть сборки на устройстве и предоставить к ним доступ другим разработчикам, использующим режим разработчика, путем [развертывания и отладки в Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) или [установки пакета приложения с помощью портала устройств](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#sideloading-applications).</span><span class="sxs-lookup"><span data-stu-id="c66f3-143">You can also deploy builds to your device and share them with other developers who have Developer Mode enabled by [deploying and debugging with Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) or [installing an application package with the Device Portal](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#sideloading-applications).</span></span>

## <a name="see-also"></a><span data-ttu-id="c66f3-144">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c66f3-144">See also</span></span>
* [<span data-ttu-id="c66f3-145">Поиск, установка и удаление приложений из Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="c66f3-145">Finding, installing, and uninstalling applications from the Microsoft Store</span></span>](/hololens/holographic-store-apps)