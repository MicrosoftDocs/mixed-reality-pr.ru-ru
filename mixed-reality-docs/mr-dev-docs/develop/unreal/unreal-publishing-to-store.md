---
title: Публикация в Microsoft Store
description: Сведения о том, как создавать пакеты ваших приложений смешанной реальности Unreal, сертифицировать и публиковать их в Microsoft Store.
author: hferrone
ms.author: jacksonf
ms.date: 12/3/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, документация, руководства, функции, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, публикация, дистрибуция, Microsoft Store
ms.openlocfilehash: 3a975d9c66e64f56919163e9d3aa65a3126d6379
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583590"
---
# <a name="publishing-to-the-microsoft-store"></a><span data-ttu-id="3c370-104">Публикация в Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="3c370-104">Publishing to the Microsoft Store</span></span>

<span data-ttu-id="3c370-105">Когда вы будете готовы представить свое приложение Unreal миру, вам потребуется настроить некоторые параметры проекта, прежде чем вы сможете отправить его в Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="3c370-105">When you're ready to get your Unreal app out to the world, there are a few project settings that need updating before you submit to the Microsoft Store.</span></span> <span data-ttu-id="3c370-106">Все эти параметры имеют значения по умолчанию, но их нужно обновить для оптимального представления приложения.</span><span class="sxs-lookup"><span data-stu-id="3c370-106">All of these settings have default values, but should be changed for production to best represent the application.</span></span>

## <a name="project-settings-for-the-store-packaging"></a><span data-ttu-id="3c370-107">Параметры упаковки проекта для публикации в магазине</span><span class="sxs-lookup"><span data-stu-id="3c370-107">Project settings for the store packaging</span></span>

1. <span data-ttu-id="3c370-108">Сначала выберите элементы **Project Settings > Description** (Параметры проекта > Описание) и измените сведения об игре и издателе:</span><span class="sxs-lookup"><span data-stu-id="3c370-108">First, select **Project Settings > Description** and update the game and publisher information:</span></span> 
    * <span data-ttu-id="3c370-109">В названии приложения в HoloLens появится **название игры**</span><span class="sxs-lookup"><span data-stu-id="3c370-109">The **Game Name** will appear in the app tile on the HoloLens</span></span>
    * <span data-ttu-id="3c370-110">**Название компании** используется при создании сертификата проекта. Оно должно иметь следующий формат:</span><span class="sxs-lookup"><span data-stu-id="3c370-110">The **Company Distinguished Name** is used when generating the project certificate and should be in the format:</span></span> 
        * <span data-ttu-id="3c370-111">**CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName**:</span><span class="sxs-lookup"><span data-stu-id="3c370-111">**CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName**:</span></span>

![Снимок экрана: Unreal Editor с развернутым разделом описания в параметрах проекта](images/unreal-publishing-img-01.png)

2. <span data-ttu-id="3c370-113">Разверните раздел **HoloLens** в параметрах проекта и измените ресурсы для упаковки.</span><span class="sxs-lookup"><span data-stu-id="3c370-113">Expand the **HoloLens** section of the project settings and update the packaging resources.</span></span>  <span data-ttu-id="3c370-114">Эти имена ресурсов будут отображаться на странице приложения в магазине:</span><span class="sxs-lookup"><span data-stu-id="3c370-114">These resource names will be shown on the application’s store page:</span></span>

![Снимок экрана: Unreal Editor с развернутым разделом упаковки в параметрах проекта](images/unreal-publishing-img-02.png)

3. <span data-ttu-id="3c370-116">Разверните раздел **Images** (Изображения) и замените изображения магазина по умолчанию текстурами, которые представляют приложение в магазине.</span><span class="sxs-lookup"><span data-stu-id="3c370-116">Expand the **Images** section and update the default store images with textures that represent the store app.</span></span>  <span data-ttu-id="3c370-117">При необходимости установите флажок **3D Logo** (Трехмерный логотип) и отправьте файл GLB для использования в качестве трехмерного анимированного куба при запуске приложения:</span><span class="sxs-lookup"><span data-stu-id="3c370-117">Optionally, select the **3D Logo** checkbox to upload a glb file to use as a 3D live cube when launching the application:</span></span>

![Снимок экрана: Unreal Editor с развернутым разделом изображений в параметрах проекта](images/unreal-publishing-img-03.png)

4. <span data-ttu-id="3c370-119">Наконец, выберите элемент **Generate New** (Создать), чтобы создать сертификат подписи из имени проекта и имени компании.</span><span class="sxs-lookup"><span data-stu-id="3c370-119">Lastly, select **Generate New** to generate a signing certificate from the project name and company distinguished name</span></span>  
    * <span data-ttu-id="3c370-120">Задайте значение для параметра **Tile Background Color** (Цвет фона плитки), который будет применяться ко всем прозрачным пикселям в изображениях магазина.</span><span class="sxs-lookup"><span data-stu-id="3c370-120">Set a **Tile Background Color**, which will appear in place of any transparent pixels in the store images.</span></span>
    * <span data-ttu-id="3c370-121">Разверните раскрывающийся список и включите параметр **Use Retail Windows Store Environment** (Использовать среду розничного магазина Windows), чтобы обеспечить выполнение приложения на устройствах с блокировкой для розничной продажи, а не для разработки.</span><span class="sxs-lookup"><span data-stu-id="3c370-121">Expand the dropdown and enable **Use Retail Windows Store Environment** to run on retail-locked, not dev-unlocked, devices.</span></span>

![Снимок экрана: Unreal Editor с развернутым разделом создания сертификата в параметрах проекта](images/unreal-publishing-img-04.png)

## <a name="optional-app-installer"></a><span data-ttu-id="3c370-123">Необязательный установщик приложения</span><span class="sxs-lookup"><span data-stu-id="3c370-123">Optional App Installer</span></span>

<span data-ttu-id="3c370-124">Файл установщика приложения можно создать в разделе **Project Settings > HoloLens** (Параметры проекта > HoloLens). Его можно использовать для дистрибуции приложения за пределами магазина.</span><span class="sxs-lookup"><span data-stu-id="3c370-124">An App Installer file can be created from **Project Settings > HoloLens**, which can be used to distribute the application outside of the store.</span></span>  <span data-ttu-id="3c370-125">Установите флажок **Should Create App Installer** (Создать установщик приложения) и задайте URL-адрес или сетевой путь, по которому будет храниться пакет appxbundle игры.</span><span class="sxs-lookup"><span data-stu-id="3c370-125">Enable the **Should Create App Installer** checkbox and set a URL or network path where you'd like the game’s appxbundle to be stored.</span></span>  

![Снимок экрана: Unreal Editor с развернутым разделом установщика приложений в параметрах проекта](images/unreal-publishing-img-05.png)

<span data-ttu-id="3c370-127">При упаковке приложения создаются файлы appxbundle и appinstaller.</span><span class="sxs-lookup"><span data-stu-id="3c370-127">When the app is being packaged, both the appxbundle and appinstaller will be generated.</span></span>  <span data-ttu-id="3c370-128">Отправьте пакет appxbundle по URL-адресу установки, а затем запустите appinstaller, чтобы установить приложение из сетевого расположения.</span><span class="sxs-lookup"><span data-stu-id="3c370-128">Upload the appxbundle to the installation URL, then launch the appinstaller to install the app from the network location.</span></span>

## <a name="windows-app-certification-kit"></a><span data-ttu-id="3c370-129">Комплект сертификации приложений для Windows</span><span class="sxs-lookup"><span data-stu-id="3c370-129">Windows App Certification Kit</span></span>

<span data-ttu-id="3c370-130">Пакет SDK для Windows 10 поставляется с комплектом сертификации приложений для Windows (WACK), позволяющим обнаруживать распространенные проблемы, которые могут повлиять на отправку пакета в магазин.</span><span class="sxs-lookup"><span data-stu-id="3c370-130">The Windows 10 SDK ships with the Windows App Certification Kit (WACK) to validate common issues that could affect uploading a package to the store.</span></span>  <span data-ttu-id="3c370-131">WACK можно найти в каталоге комплектов для Windows, который обычно располагается по следующему пути:</span><span class="sxs-lookup"><span data-stu-id="3c370-131">You can find the WACK in the Windows Kits directory, usually under the following path:</span></span> 

```
C:\Program Files (x86)\Windows Kits\10\App Certification Kit.
```

1. <span data-ttu-id="3c370-132">После упаковки файла appx для публикации запустите файл **appcertui.exe** и следуйте инструкциям, чтобы проверить appx:</span><span class="sxs-lookup"><span data-stu-id="3c370-132">After your appx file is packaged for publication, run **appcertui.exe** and follow the prompts to scan the appx:</span></span>

![Снимок экрана: выбор приложения для проверки в комплекте сертификации приложений для Windows](images/unreal-publishing-img-06.png)

2. <span data-ttu-id="3c370-134">Выберите элемент **Validate Store App** (Проверить приложение магазина):</span><span class="sxs-lookup"><span data-stu-id="3c370-134">Select **Validate Store App**:</span></span>

![Снимок экрана: выбор проверки в комплекте сертификации приложений для Windows](images/unreal-publishing-img-07.png)

3. <span data-ttu-id="3c370-136">Найдите appx в верхнем разделе и нажмите кнопку **Далее**:</span><span class="sxs-lookup"><span data-stu-id="3c370-136">Browse for the appx in the top section and select **Next**:</span></span>

![Снимок экрана: выбор теста в комплекте сертификации приложений Windows](images/unreal-publishing-img-08.png)

4. <span data-ttu-id="3c370-138">Нажмите кнопку **Далее**, чтобы запустить тесты и создать отчет:</span><span class="sxs-lookup"><span data-stu-id="3c370-138">Select **Next** to run the tests and create a report:</span></span>
    * <span data-ttu-id="3c370-139">Все доступные тесты, которые можно выполнить на компьютере размещения, будут включены по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="3c370-139">All available tests that can be run on the host PC will be enabled by default</span></span>

![Снимок экрана: ход проверки приложения в комплекте сертификации приложений для Windows](images/unreal-publishing-img-09.png)

5. <span data-ttu-id="3c370-141">Дождитесь завершения тестов.</span><span class="sxs-lookup"><span data-stu-id="3c370-141">Wait for the tests to finish.</span></span> <span data-ttu-id="3c370-142">По их завершении в последнем окне отобразится результат (пройдено или не пройдено), который также можно просмотреть в сохраненном отчете.</span><span class="sxs-lookup"><span data-stu-id="3c370-142">Once complete, the final window will show a pass or fail result, which can be viewed in the saved report.</span></span>

![Снимок экрана: финальные результаты в комплекте сертификации приложений для Windows](images/unreal-publishing-img-10.png)

## <a name="known-wack-failure-with-425"></a><span data-ttu-id="3c370-144">Известный сбой WACK с версией 4.25</span><span class="sxs-lookup"><span data-stu-id="3c370-144">Known WACK failure with 4.25</span></span>

<span data-ttu-id="3c370-145">Подключаемый модуль Windows Mixed Reality в Unreal 4.25 будет завершаться со сбоем при работе WACK, так как при упаковке для HoloLens в пакет включаются некоторые 64-разрядные двоичные файлы.</span><span class="sxs-lookup"><span data-stu-id="3c370-145">The Windows Mixed Reality plugin in Unreal 4.25 will fail WACK because some x64 binaries are included while packaging for HoloLens.</span></span> <span data-ttu-id="3c370-146">При сбое будет отображаться следующее:</span><span class="sxs-lookup"><span data-stu-id="3c370-146">The failure will look like this:</span></span>

![Снимок экрана: сбой получения результата, связанный с анализатором двоичных файлов и поддерживаемыми API, в комплекте сертификации приложений для Windows](images/unreal-publishing-img-11.png)

<span data-ttu-id="3c370-148">Чтобы исправить проблему</span><span class="sxs-lookup"><span data-stu-id="3c370-148">To fix the issue:</span></span>
1. <span data-ttu-id="3c370-149">Перейдите к установке Unreal или исходному корневому каталогу. Для этого откройте проект Unreal и щелкните значок Unreal на панели задач правой кнопкой мыши.</span><span class="sxs-lookup"><span data-stu-id="3c370-149">Browse to the Unreal installation or source directory root by opening an Unreal project and right-click on the Unreal icon in the taskbar.</span></span>
2. <span data-ttu-id="3c370-150">Щелкните правой кнопкой мыши UE4Editor, выберите пункт "Свойства" и перейдите по пути в пункте **Расположение**:</span><span class="sxs-lookup"><span data-stu-id="3c370-150">Right-click on UE4Editor, select properties, and browse to the path in the **Location** entry:</span></span>

```
Open Engine\Plugins\Runtime\WindowsMixedReality\Source\WindowsMixedRealityHMD\WindowsMixedRealityHMD.Build.cs.
```

3. <span data-ttu-id="3c370-151">В файле **WindowsMixedRealityHMD.Build.cs** измените **строку 32** с:</span><span class="sxs-lookup"><span data-stu-id="3c370-151">In **WindowsMixedRealityHMD.Build.cs**, modify **line 32** from:</span></span>

```cpp
if(Target.Platform != UnrealTargetPlatform.Win32)
```

<span data-ttu-id="3c370-152">на:</span><span class="sxs-lookup"><span data-stu-id="3c370-152">to:</span></span>

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64)

```

4. <span data-ttu-id="3c370-153">Закройте Unreal, откройте проект и выполните повторную сборку пакета для HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3c370-153">Close Unreal, reopen the project, and repackage for HoloLens.</span></span>  <span data-ttu-id="3c370-154">Перезапустите WACK, и ошибка исчезнет.</span><span class="sxs-lookup"><span data-stu-id="3c370-154">Rerun WACK and the error will be gone.</span></span> 

## <a name="see-also"></a><span data-ttu-id="3c370-155">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="3c370-155">See also</span></span>

* [<span data-ttu-id="3c370-156">Отправка приложения в Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="3c370-156">Submitting an app to the Microsoft Store</span></span>](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [<span data-ttu-id="3c370-157">Комплект сертификации приложений для Windows</span><span class="sxs-lookup"><span data-stu-id="3c370-157">Windows App Certification Kit</span></span>](https://developer.microsoft.com/windows/downloads/app-certification-kit)
* [<span data-ttu-id="3c370-158">Создание файла Установщика приложений вручную</span><span class="sxs-lookup"><span data-stu-id="3c370-158">Create an App Installer file manually</span></span>](/windows/msix/app-installer/how-to-create-appinstaller-file)