---
title: Вас приветствует Mixed Reality Feature Tool
description: Основные сведения о средстве Mixed Reality Feature Tool и его использовании для разработки для HoloLens и виртуальной реальности.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: актуальность, инструменты, начало работы, основы, Unity, Visual Studio, набор средств, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, установка, Windows, HoloLens, эмулятор, Unreal, OpenXR
ms.openlocfilehash: 4e822f2dda2a314ce06bc394a4d92b1aa6953af3
ms.sourcegitcommit: 943489923c69c3a28bc152f1cb516dcdcea2880a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2021
ms.locfileid: "111772417"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a><span data-ttu-id="35cc2-104">Вас приветствует Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="35cc2-104">Welcome to the Mixed Reality Feature Tool</span></span>

![Изображение баннера Mixed Reality Feature Tool](images/feature-tool-banner.png)

> [!IMPORTANT]
> <span data-ttu-id="35cc2-106">В данный момент средство Mixed Reality Feature Tool доступно только для платформы Unity.</span><span class="sxs-lookup"><span data-stu-id="35cc2-106">The Mixed Reality Feature Tool is only available for Unity at the moment.</span></span> <span data-ttu-id="35cc2-107">Если вы ведете разработку в Unreal, перейдите к документации по [установке средств](../install-the-tools.md) для этого движка.</span><span class="sxs-lookup"><span data-stu-id="35cc2-107">If you're developing in Unreal, refer to the [tools installation](../install-the-tools.md) documentation.</span></span>

<span data-ttu-id="35cc2-108">Средство Mixed Reality Feature Tool предоставляет новый способ для обнаружения, обновления и добавления пакетов функций смешанной реальности в проекты Unity.</span><span class="sxs-lookup"><span data-stu-id="35cc2-108">The Mixed Reality Feature Tool is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="35cc2-109">Вы можете искать пакеты по имени или категории, просматривать их зависимости и даже проверять предлагаемые изменения в файле манифеста проектов перед импортом.</span><span class="sxs-lookup"><span data-stu-id="35cc2-109">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="35cc2-110">Поясним для тех, кто еще не работал с файлом манифеста: это файл в формате JSON, который содержит все пакеты проектов.</span><span class="sxs-lookup"><span data-stu-id="35cc2-110">If you've never worked with a manifest file before, it's a JSON file containing all your projects packages.</span></span> <span data-ttu-id="35cc2-111">Когда вы подтвердите список нужных пакетов, средство Mixed Reality Feature Tool скачает их в выбранный вами проект.</span><span class="sxs-lookup"><span data-stu-id="35cc2-111">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="35cc2-112">Требования к системе</span><span class="sxs-lookup"><span data-stu-id="35cc2-112">System requirements</span></span>

<span data-ttu-id="35cc2-113">Перед запуском средства Mixed Reality Feature Tool вам потребуется следующее:</span><span class="sxs-lookup"><span data-stu-id="35cc2-113">Before you can run the Mixed Reality Feature Tool, you'll need:</span></span>

* <span data-ttu-id="35cc2-114">[среда выполнения .NET 5.0](https://dotnet.microsoft.com/download/dotnet/5.0);</span><span class="sxs-lookup"><span data-stu-id="35cc2-114">[.NET 5.0 runtime](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
* [<span data-ttu-id="35cc2-115">Windows 10</span><span class="sxs-lookup"><span data-stu-id="35cc2-115">Windows 10</span></span>](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> <span data-ttu-id="35cc2-116">В настоящее время средство Mixed Reality Feature Tool работает только в Windows, но скоро станет доступна поддержка MacOS.</span><span class="sxs-lookup"><span data-stu-id="35cc2-116">The Mixed Reality Feature Tool currently only runs on Windows, but MacOS support is coming soon!</span></span>

## <a name="download"></a><span data-ttu-id="35cc2-117">Скачивание</span><span class="sxs-lookup"><span data-stu-id="35cc2-117">Download</span></span>

<span data-ttu-id="35cc2-118">После настройки среды выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="35cc2-118">Once you have your environment set up:</span></span>

* <span data-ttu-id="35cc2-119">[Скачайте последнюю версию средства Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool) из Центра загрузки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="35cc2-119">[Download the latest version of the Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool) from the Microsoft Download Center.</span></span>
* <span data-ttu-id="35cc2-120">Когда скачивание завершится, распакуйте файл и сохраните его на рабочем столе.</span><span class="sxs-lookup"><span data-stu-id="35cc2-120">When the download completes, unzip the file and save it to your desktop</span></span>
    * <span data-ttu-id="35cc2-121">Для упрощения доступа рекомендуется создать ярлык для исполняемого файла.</span><span class="sxs-lookup"><span data-stu-id="35cc2-121">We recommend creating a shortcut to the executable file for faster access</span></span>

> [!NOTE]
> <span data-ttu-id="35cc2-122">Если вы не знакомы с использованием диспетчера пакетов Unity, следуйте нашим [инструкциям по UPM](/windows/mixed-reality/mrtk-unity/configuration/usingupm#managing-mixed-reality-features-with-the-unity-package-manager).</span><span class="sxs-lookup"><span data-stu-id="35cc2-122">If you're new to using the Unity Package Manager, follow our [UPM instructions](/windows/mixed-reality/mrtk-unity/configuration/usingupm#managing-mixed-reality-features-with-the-unity-package-manager).</span></span>

## <a name="changes-in-this-release"></a><span data-ttu-id="35cc2-123">Изменения в этом выпуске</span><span class="sxs-lookup"><span data-stu-id="35cc2-123">Changes in this release</span></span>

<span data-ttu-id="35cc2-124">Бета-версия 1.0.2103 включает следующие исправления:</span><span class="sxs-lookup"><span data-stu-id="35cc2-124">Version 1.0.2103 Beta includes the following fixes:</span></span>

* <span data-ttu-id="35cc2-125">улучшено обнаружение ошибок при скачивании;</span><span class="sxs-lookup"><span data-stu-id="35cc2-125">Improvements to download error detection.</span></span>
* <span data-ttu-id="35cc2-126">обновлен способ написания манифестов для избежания ошибок при обновлении;</span><span class="sxs-lookup"><span data-stu-id="35cc2-126">Updates on how manifests are written to avoid failure to update correctly.</span></span>
* <span data-ttu-id="35cc2-127">удалено экранирование из путей к файлам в манифесте проекта.</span><span class="sxs-lookup"><span data-stu-id="35cc2-127">Escpaing has been removed from file paths in the project manifest.</span></span>

<span data-ttu-id="35cc2-128">В этом выпуске добавлены следующие функции:</span><span class="sxs-lookup"><span data-stu-id="35cc2-128">The following features have been added in this release:</span></span>

* <span data-ttu-id="35cc2-129">кэширование каталога компонентов;</span><span class="sxs-lookup"><span data-stu-id="35cc2-129">The feature catalog is now cached.</span></span> <span data-ttu-id="35cc2-130">для проверки наличия обновлений и новых функций теперь можно нажать кнопку "Обновить" в окне обнаружения;</span><span class="sxs-lookup"><span data-stu-id="35cc2-130">To check for new features and updates, please use the refresh button in Discovery.</span></span>
* <span data-ttu-id="35cc2-131">возможность перемещать выбранный проект из шага импорта перед обнаружением;</span><span class="sxs-lookup"><span data-stu-id="35cc2-131">Move project selection from the Import step to before Discovery.</span></span>
* <span data-ttu-id="35cc2-132">фильтрация доступных пакетов по указанной в проекте версии Unity;</span><span class="sxs-lookup"><span data-stu-id="35cc2-132">Available packages are filtered by the project's specified Unity version.</span></span>
* <span data-ttu-id="35cc2-133">в окне обнаружения теперь отображаются установленные пакеты.</span><span class="sxs-lookup"><span data-stu-id="35cc2-133">The discovery view now displays currently installed packages.</span></span>

## <a name="1-getting-started"></a><span data-ttu-id="35cc2-134">1. Начало работы</span><span class="sxs-lookup"><span data-stu-id="35cc2-134">1. Getting started</span></span>

<span data-ttu-id="35cc2-135">Запустите средство Mixed Reality Feature Tool из исполняемого файла. При первом запуске отобразится такая начальная страница:</span><span class="sxs-lookup"><span data-stu-id="35cc2-135">Launch the Mixed Reality Feature Tool from the executable file, which displays the start page on first launch:</span></span>

![Начало работы](images/FeatureToolStart.png)

<span data-ttu-id="35cc2-137">На этой странице можно выполнить следующие действия:</span><span class="sxs-lookup"><span data-stu-id="35cc2-137">From the start page, you can:</span></span>

* <span data-ttu-id="35cc2-138">[настроить параметры средства](configuring-feature-tool.md) с помощью кнопки со **значком шестеренки**;</span><span class="sxs-lookup"><span data-stu-id="35cc2-138">[Configure](configuring-feature-tool.md) tool settings using the **gear icon** button</span></span>
* <span data-ttu-id="35cc2-139">открыть веб-браузер, настроенный по умолчанию, и отобразить нашу документацию с помощью кнопки со **значком вопросительного знака**;</span><span class="sxs-lookup"><span data-stu-id="35cc2-139">Use the **question mark** button to launch the default web browser and display our documentation</span></span>
* <span data-ttu-id="35cc2-140">щелкнуть **кнопку запуска**, чтобы начать обнаружение пакетов функций.</span><span class="sxs-lookup"><span data-stu-id="35cc2-140">Select **Start** to begin discovering feature packages</span></span>

## <a name="2-selecting-your-unity-project"></a><span data-ttu-id="35cc2-141">2. Выбор проекта Unity</span><span class="sxs-lookup"><span data-stu-id="35cc2-141">2. Selecting your Unity project</span></span>

<span data-ttu-id="35cc2-142">Чтобы все обнаруженные функции поддерживались в версии Unity вашего проекта, сначала укажите в проекте Mixed Reality Feature Tool, щелкнув кнопку **с многоточием** (справа от поля пути проекта).</span><span class="sxs-lookup"><span data-stu-id="35cc2-142">To ensure that all discovered features are supported on your project's version of Unity, the fist step is to point the Mixed Reality Feature Tool to your project using the **ellipsis** button (to the right of the project path field).</span></span>

![Выбор проекта Unity](images/FeatureToolSelectUnityProject.png)

> [!NOTE]
> <span data-ttu-id="35cc2-144">При просмотре папки проекта Unity отображается диалоговое окно, где в качестве имени файла указан символ "_".</span><span class="sxs-lookup"><span data-stu-id="35cc2-144">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="35cc2-145">Чтобы получить возможность выбрать папку, для этого файла необходимо указать значение имени.</span><span class="sxs-lookup"><span data-stu-id="35cc2-145">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="35cc2-146">После того как вы нашли папку проекта, нажмите кнопку "Открыть", чтобы вернуться к средству Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="35cc2-146">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="35cc2-147">Средство Mixed Reality Feature Tool выполнит проверку того, что оно направлено в папку проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="35cc2-147">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="35cc2-148">Папка должна содержать папки `Assets`, `Packages` и `Project Settings`.</span><span class="sxs-lookup"><span data-stu-id="35cc2-148">The folder must contain `Assets`, `Packages` and `Project Settings` folders.</span></span>

## <a name="3-discovering-and-acquiring-feature-packages"></a><span data-ttu-id="35cc2-149">3. Обнаружение и получение пакетов функций</span><span class="sxs-lookup"><span data-stu-id="35cc2-149">3. Discovering and acquiring feature packages</span></span>

> [!NOTE]
> <span data-ttu-id="35cc2-150">В бета-версии 1.0.2103 теперь кэшируется содержимое каталога компонентов при каждом доступе к серверу.</span><span class="sxs-lookup"><span data-stu-id="35cc2-150">Version 1.0.2103 Beta now caches the feature catalog contents whenever the server is accessed.</span></span> <span data-ttu-id="35cc2-151">Это изменение обеспечивает быстрый доступ к возможным функциям за счет отображения самых последних данных.</span><span class="sxs-lookup"><span data-stu-id="35cc2-151">This change enables fast access to available features, at the expense of displaying the absolute latest data.</span></span> <span data-ttu-id="35cc2-152">Чтобы обновить каталог, нажмите кнопку **Refresh** (Обновить).</span><span class="sxs-lookup"><span data-stu-id="35cc2-152">To update the catalog, please use the **Refresh** button.</span></span>

<span data-ttu-id="35cc2-153">Функции группируются по категориям, чтобы их было проще найти.</span><span class="sxs-lookup"><span data-stu-id="35cc2-153">Features are grouped by category to make things easier to find.</span></span> <span data-ttu-id="35cc2-154">Например, категория **Mixed Reality Toolkit** содержит несколько вариантов для выбора:</span><span class="sxs-lookup"><span data-stu-id="35cc2-154">For example, the **Mixed Reality Toolkit** category has several features for you to choose from:</span></span>

![Обнаружение и получение](images/FeatureToolDiscovery.png)

<span data-ttu-id="35cc2-156">Когда средство Mixed Reality Feature Tool обнаруживает ранее импортированные функции, оно отображает уведомление о каждой из них.</span><span class="sxs-lookup"><span data-stu-id="35cc2-156">When the Mixed Reality Feature Tool recognizes previously imported feature(s), it displays a notification message by each.</span></span>

![Уведомление об импортированной функции](images/feature-tool-imported-note.png)


<span data-ttu-id="35cc2-158">Завершив выбор вариантов, щелкните **Get features** (Получить функции), чтобы извлечь из каталога все необходимые пакеты.</span><span class="sxs-lookup"><span data-stu-id="35cc2-158">Once you've made your choices, select **Get features** to fetch all the required packages from the catalog.</span></span> <span data-ttu-id="35cc2-159">Дополнительные сведения см. в статье [Обнаружение и получение функций](discovering-features.md).</span><span class="sxs-lookup"><span data-stu-id="35cc2-159">For more information, please see [discovering and acquiring features](discovering-features.md).</span></span>

## <a name="4-importing-feature-packages"></a><span data-ttu-id="35cc2-160">4. Импорт пакетов функций</span><span class="sxs-lookup"><span data-stu-id="35cc2-160">4. Importing feature packages</span></span>

<span data-ttu-id="35cc2-161">После приобретения вам будет представлен полный набор пакетов и список необходимых зависимостей.</span><span class="sxs-lookup"><span data-stu-id="35cc2-161">Following acquisition, the complete set of packages is presented, along with a list of required dependencies.</span></span> <span data-ttu-id="35cc2-162">Если вам нужно изменить выбранные функции или пакеты, это следует сделать сейчас:</span><span class="sxs-lookup"><span data-stu-id="35cc2-162">If you need to change any feature or package selections, this is the time:</span></span>

![Импорт пакетов](images/FeatureToolImport.png)

<span data-ttu-id="35cc2-164">Мы настоятельно рекомендуем использовать кнопку **Validate** (Проверить), чтобы проект Unity смог успешно импортировать выбранные функции.</span><span class="sxs-lookup"><span data-stu-id="35cc2-164">We highly recommend using the **Validate** button to ensure the Unity project can successfully import the selected features.</span></span> <span data-ttu-id="35cc2-165">После проверки вы увидите всплывающее диалоговое окно с сообщением об успешном выполнении или списком выявленных проблем.</span><span class="sxs-lookup"><span data-stu-id="35cc2-165">After validation, you'll see a pop-up dialog with a success message or a list of identified issues.</span></span>

<span data-ttu-id="35cc2-166">Чтобы продолжить, щелкните **Import** (Импортировать).</span><span class="sxs-lookup"><span data-stu-id="35cc2-166">Select **Import** to continue.</span></span>

> [!NOTE]
> <span data-ttu-id="35cc2-167">После нажатия кнопки **Import** (Импортировать) отобразится простое сообщение, если остались нерешенные проблемы.</span><span class="sxs-lookup"><span data-stu-id="35cc2-167">After clicking the **Import** button, if any issues remain a simple message will be displayed.</span></span> <span data-ttu-id="35cc2-168">Мы рекомендуем нажать здесь кнопку "Нет" и щелкнуть **Validate** (Проверить), чтобы просмотреть и устранить эти проблемы.</span><span class="sxs-lookup"><span data-stu-id="35cc2-168">The recommendation is to click No and to use the **Validate** button to view and resolve the issues.</span></span>

<span data-ttu-id="35cc2-169">Дополнительные сведения см. в статье об [импорте функций](importing-features.md).</span><span class="sxs-lookup"><span data-stu-id="35cc2-169">For more information, please see [importing features](importing-features.md).</span></span>

## <a name="5-reviewing-and-approving-project-changes"></a><span data-ttu-id="35cc2-170">5. Просмотр и утверждение изменений в проекте</span><span class="sxs-lookup"><span data-stu-id="35cc2-170">5. Reviewing and approving project changes</span></span>

<span data-ttu-id="35cc2-171">Последним шагом станет проверка и утверждение предложенных изменений в файлах манифеста и проекта:</span><span class="sxs-lookup"><span data-stu-id="35cc2-171">The final step is reviewing and approving the proposed changes to the manifest and project files:</span></span>

* <span data-ttu-id="35cc2-172">Слева отображаются предлагаемые изменения в манифесте.</span><span class="sxs-lookup"><span data-stu-id="35cc2-172">The proposed changes to the manifest are displayed on the left</span></span>
* <span data-ttu-id="35cc2-173">Справа приведены файлы, которые будут добавлены в проект.</span><span class="sxs-lookup"><span data-stu-id="35cc2-173">The files to be added to the project are listed to the right</span></span>
* <span data-ttu-id="35cc2-174">Кнопка **Compare** (Сравнить) позволяет просматривать в двух соседних окнах текущую версию манифеста и предлагаемые изменения.</span><span class="sxs-lookup"><span data-stu-id="35cc2-174">The **Compare** button allows for side by side viewing of the current manifest and the proposed changes</span></span>

![Авторизация](images/FeatureToolApprovalRequest.png)

<span data-ttu-id="35cc2-176">Дополнительные сведения см. в статье [Просмотр и утверждение изменений в проекте](reviewing-changes.md).</span><span class="sxs-lookup"><span data-stu-id="35cc2-176">For more information, see [reviewing and approving project modifications](reviewing-changes.md).</span></span>

## <a name="6-project-updated"></a><span data-ttu-id="35cc2-177">6. Обновленный проект</span><span class="sxs-lookup"><span data-stu-id="35cc2-177">6. Project updated</span></span>

<span data-ttu-id="35cc2-178">После утверждения предложенных изменений будет обновлен целевой проект Unity, чтобы он содержал ссылки на выбранные функции смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="35cc2-178">When the proposed changes are approved, your target Unity project is updated to reference the selected Mixed Reality features.</span></span>

![Проект обновлен](images/FeatureToolProjectUpdated.png)

<span data-ttu-id="35cc2-180">В папке **Packages** проекта Unity теперь содержится вложенная папка **MixedReality** с файлами пакетов функций, а манифест будет содержать соответствующие ссылки.</span><span class="sxs-lookup"><span data-stu-id="35cc2-180">The Unity project's **Packages** folder now has a **MixedReality** subfolder with the feature package file(s) and the manifest will contain the appropriate reference(s).</span></span>

<span data-ttu-id="35cc2-181">Вернитесь в Unity, дождитесь загрузки новых функций и приступайте к разработке.</span><span class="sxs-lookup"><span data-stu-id="35cc2-181">Return to Unity, wait for the new selected features to load, and start building!</span></span>

## <a name="see-also"></a><span data-ttu-id="35cc2-182">См. также</span><span class="sxs-lookup"><span data-stu-id="35cc2-182">See also</span></span>

- [<span data-ttu-id="35cc2-183">Настройка средства функций</span><span class="sxs-lookup"><span data-stu-id="35cc2-183">Configuring the feature tool</span></span>](configuring-feature-tool.md)
- [<span data-ttu-id="35cc2-184">Обнаружение и получение</span><span class="sxs-lookup"><span data-stu-id="35cc2-184">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="35cc2-185">Просмотр сведений о пакете функций</span><span class="sxs-lookup"><span data-stu-id="35cc2-185">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="35cc2-186">Импорт выбранных пакетов</span><span class="sxs-lookup"><span data-stu-id="35cc2-186">Importing selected packages</span></span>](importing-features.md)
- [<span data-ttu-id="35cc2-187">Просмотр и утверждение изменений в проекте</span><span class="sxs-lookup"><span data-stu-id="35cc2-187">Reviewing and approving project modifications</span></span>](reviewing-changes.md)