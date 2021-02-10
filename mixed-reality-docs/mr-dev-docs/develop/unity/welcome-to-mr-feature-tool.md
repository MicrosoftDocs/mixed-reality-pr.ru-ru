---
title: Вас приветствует Mixed Reality Feature Tool
description: Основные сведения о средстве Mixed Reality Feature Tool и его использовании для разработки для HoloLens и виртуальной реальности.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: актуальность, инструменты, начало работы, основы, Unity, Visual Studio, набор средств, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, установка, Windows, HoloLens, эмулятор, Unreal, OpenXR
ms.openlocfilehash: 0aad81ddd625467dd9159232d590b1a4bf68d06b
ms.sourcegitcommit: d9f87635c87627adba7db37834e4627c149f9a28
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/05/2021
ms.locfileid: "99570257"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a><span data-ttu-id="946b2-104">Вас приветствует Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="946b2-104">Welcome to the Mixed Reality Feature Tool</span></span>

![Изображение баннера Mixed Reality Feature Tool](images/feature-tool-banner.png)

> [!IMPORTANT]
> <span data-ttu-id="946b2-106">В данный момент средство Mixed Reality Feature Tool доступно только для платформы Unity.</span><span class="sxs-lookup"><span data-stu-id="946b2-106">The Mixed Reality Feature Tool is only available for Unity at the moment.</span></span> <span data-ttu-id="946b2-107">Если вы ведете разработку в Unreal, перейдите к документации по [установке средств](../install-the-tools.md) для этого движка.</span><span class="sxs-lookup"><span data-stu-id="946b2-107">If you're developing in Unreal, refer to the [tools installation](../install-the-tools.md) documentation.</span></span>

<span data-ttu-id="946b2-108">Средство Mixed Reality Feature Tool предоставляет новый способ для обнаружения, обновления и добавления пакетов функций смешанной реальности в проекты Unity.</span><span class="sxs-lookup"><span data-stu-id="946b2-108">The Mixed Reality Feature Tool is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="946b2-109">Вы можете искать пакеты по имени или категории, просматривать их зависимости и даже проверять предлагаемые изменения в файле манифеста проектов перед импортом.</span><span class="sxs-lookup"><span data-stu-id="946b2-109">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="946b2-110">Поясним для тех, кто еще не работал с файлом манифеста: это файл в формате JSON, который содержит все пакеты проектов.</span><span class="sxs-lookup"><span data-stu-id="946b2-110">If you've never worked with a manifest file before, it's a JSON file containing all your projects packages.</span></span> <span data-ttu-id="946b2-111">Когда вы подтвердите список нужных пакетов, средство Mixed Reality Feature Tool скачает их в выбранный вами проект.</span><span class="sxs-lookup"><span data-stu-id="946b2-111">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="946b2-112">Требования к системе</span><span class="sxs-lookup"><span data-stu-id="946b2-112">System requirements</span></span>

<span data-ttu-id="946b2-113">Перед запуском средства Mixed Reality Feature Tool вам потребуется следующее:</span><span class="sxs-lookup"><span data-stu-id="946b2-113">Before you can run the Mixed Reality Feature Tool, you'll need:</span></span>

* <span data-ttu-id="946b2-114">[среда выполнения .NET 5.0](https://dotnet.microsoft.com/download/dotnet/5.0);</span><span class="sxs-lookup"><span data-stu-id="946b2-114">[.NET 5.0 runtime](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
* [<span data-ttu-id="946b2-115">Windows 10</span><span class="sxs-lookup"><span data-stu-id="946b2-115">Windows 10</span></span>](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> <span data-ttu-id="946b2-116">В настоящее время средство Mixed Reality Feature Tool работает только в Windows, но скоро станет доступна поддержка MacOS.</span><span class="sxs-lookup"><span data-stu-id="946b2-116">The Mixed Reality Feature Tool currently only runs on Windows, but MacOS support is coming soon!</span></span>

## <a name="download"></a><span data-ttu-id="946b2-117">Скачивание</span><span class="sxs-lookup"><span data-stu-id="946b2-117">Download</span></span> 

<span data-ttu-id="946b2-118">После настройки среды выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="946b2-118">Once you have your environment set up:</span></span>

* <span data-ttu-id="946b2-119">[Скачайте последнюю версию средства Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool) из Центра загрузки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="946b2-119">[Download the latest version of the Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool) from the Microsoft Download Center.</span></span>
* <span data-ttu-id="946b2-120">Когда скачивание завершится, распакуйте файл и сохраните его на рабочем столе.</span><span class="sxs-lookup"><span data-stu-id="946b2-120">When the download completes, unzip the file and save it to your desktop</span></span>
    * <span data-ttu-id="946b2-121">Для упрощения доступа рекомендуется создать ярлык для исполняемого файла.</span><span class="sxs-lookup"><span data-stu-id="946b2-121">We recommend creating a shortcut to the executable file for faster access</span></span>

## <a name="1-getting-started"></a><span data-ttu-id="946b2-122">1. Начало работы</span><span class="sxs-lookup"><span data-stu-id="946b2-122">1. Getting started</span></span>

<span data-ttu-id="946b2-123">Запустите средство Mixed Reality Feature Tool из исполняемого файла. При первом запуске отобразится такая начальная страница:</span><span class="sxs-lookup"><span data-stu-id="946b2-123">Launch the Mixed Reality Feature Tool from the executable file, which displays the start page on first launch:</span></span>

![Начало работы](images/FeatureToolStart.png)

<span data-ttu-id="946b2-125">На этой странице можно выполнить следующие действия:</span><span class="sxs-lookup"><span data-stu-id="946b2-125">From the start page, you can:</span></span>

* <span data-ttu-id="946b2-126">[настроить параметры средства](configuring-feature-tool.md) с помощью кнопки со **значком шестеренки**;</span><span class="sxs-lookup"><span data-stu-id="946b2-126">[Configure](configuring-feature-tool.md) tool settings using the **gear icon** button</span></span>
* <span data-ttu-id="946b2-127">открыть веб-браузер, настроенный по умолчанию, и отобразить нашу документацию с помощью кнопки со **значком вопросительного знака**;</span><span class="sxs-lookup"><span data-stu-id="946b2-127">Use the **question mark** button to launch the default web browser and display our documentation</span></span>
* <span data-ttu-id="946b2-128">щелкнуть **кнопку запуска**, чтобы начать обнаружение пакетов функций.</span><span class="sxs-lookup"><span data-stu-id="946b2-128">Select **Start** to begin discovering feature packages</span></span>

## <a name="2-discovering-and-acquiring-feature-packages"></a><span data-ttu-id="946b2-129">2. Обнаружение и получение пакетов функций</span><span class="sxs-lookup"><span data-stu-id="946b2-129">2. Discovering and acquiring feature packages</span></span>

<span data-ttu-id="946b2-130">Каталог пакетов функций извлекается сразу после нажатия кнопки Start (Пуск).</span><span class="sxs-lookup"><span data-stu-id="946b2-130">The feature package catalog is retrieved as soon as you press Start.</span></span> <span data-ttu-id="946b2-131">Функции группируются по категориям, чтобы их было проще найти.</span><span class="sxs-lookup"><span data-stu-id="946b2-131">Features are grouped by category to make things easier to find.</span></span> <span data-ttu-id="946b2-132">Например, категория **Mixed Reality Toolkit** содержит несколько вариантов для выбора:</span><span class="sxs-lookup"><span data-stu-id="946b2-132">For example, the **Mixed Reality Toolkit** category has several features for you to choose from:</span></span>

![Обнаружение и получение](images/FeatureToolDiscovery.png)

<span data-ttu-id="946b2-134">Завершив выбор вариантов, щелкните **Get features** (Получить функции), чтобы извлечь из каталога все необходимые пакеты.</span><span class="sxs-lookup"><span data-stu-id="946b2-134">Once you've made your choices, select **Get features** to fetch all the required packages from the catalog.</span></span> <span data-ttu-id="946b2-135">Дополнительные сведения см. в статье [Обнаружение и получение функций](discovering-features.md).</span><span class="sxs-lookup"><span data-stu-id="946b2-135">For more information, please see [discovering and acquiring features](discovering-features.md).</span></span>

## <a name="3-importing-feature-packages"></a><span data-ttu-id="946b2-136">3. Импорт пакетов функций</span><span class="sxs-lookup"><span data-stu-id="946b2-136">3. Importing feature packages</span></span>

<span data-ttu-id="946b2-137">После приобретения вам будет представлен полный набор пакетов и список необходимых зависимостей.</span><span class="sxs-lookup"><span data-stu-id="946b2-137">Following acquisition, the complete set of packages is presented, along with a list of required dependencies.</span></span> <span data-ttu-id="946b2-138">Если вам нужно изменить выбранные функции или пакеты, это следует сделать сейчас:</span><span class="sxs-lookup"><span data-stu-id="946b2-138">If you need to change any feature or package selections, this is the time:</span></span>

![Импорт пакетов](images/FeatureToolImport.png)

<span data-ttu-id="946b2-140">Мы настоятельно рекомендуем использовать кнопку **Validate** (Проверить), чтобы проект Unity смог успешно импортировать выбранные функции.</span><span class="sxs-lookup"><span data-stu-id="946b2-140">We highly recommend using the **Validate** button to ensure the Unity project can successfully import the selected features.</span></span> <span data-ttu-id="946b2-141">После проверки вы увидите всплывающее диалоговое окно с сообщением об успешном выполнении или списком выявленных проблем.</span><span class="sxs-lookup"><span data-stu-id="946b2-141">After validation, you'll see a pop-up dialog with a success message or a list of identified issues.</span></span>

<span data-ttu-id="946b2-142">Перед импортом необходимо также задать расположение целевого проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="946b2-142">You also need to set the location of the target Unity project before you import.</span></span> <span data-ttu-id="946b2-143">Нажмите кнопку с **символом многоточия**, расположенную слева от поля для пути к проекту, чтобы просмотреть папки.</span><span class="sxs-lookup"><span data-stu-id="946b2-143">Use the **ellipsis** button to the left of the project path field to browse.</span></span> <span data-ttu-id="946b2-144">Найдите в файловой системе и откройте папку, которая содержит целевой проект Unity.</span><span class="sxs-lookup"><span data-stu-id="946b2-144">When you're done navigating your file system, open the folder containing your target Unity project.</span></span>

> [!NOTE]
> <span data-ttu-id="946b2-145">При просмотре папки проекта Unity отображается диалоговое окно, где в качестве имени файла указан символ "_".</span><span class="sxs-lookup"><span data-stu-id="946b2-145">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="946b2-146">Чтобы получить возможность выбрать папку, для этого файла необходимо указать значение имени.</span><span class="sxs-lookup"><span data-stu-id="946b2-146">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="946b2-147">Чтобы продолжить, щелкните **Import** (Импортировать).</span><span class="sxs-lookup"><span data-stu-id="946b2-147">Select **Import** to continue.</span></span>

> [!NOTE]
> <span data-ttu-id="946b2-148">После нажатия кнопки **Import** (Импортировать) отобразится простое сообщение, если остались нерешенные проблемы.</span><span class="sxs-lookup"><span data-stu-id="946b2-148">After clicking the **Import** button, if any issues remain a simple message will be displayed.</span></span> <span data-ttu-id="946b2-149">Мы рекомендуем нажать здесь кнопку "Нет" и щелкнуть **Validate** (Проверить), чтобы просмотреть и устранить эти проблемы.</span><span class="sxs-lookup"><span data-stu-id="946b2-149">The recommendation is to click No and to use the **Validate** button to view and resolve the issues.</span></span>

<span data-ttu-id="946b2-150">Дополнительные сведения см. в статье об [импорте функций](importing-features.md).</span><span class="sxs-lookup"><span data-stu-id="946b2-150">For more information, please see [importing features](importing-features.md).</span></span>

## <a name="4-reviewing-and-approving-project-changes"></a><span data-ttu-id="946b2-151">4. Просмотр и утверждение изменений в проекте</span><span class="sxs-lookup"><span data-stu-id="946b2-151">4. Reviewing and approving project changes</span></span>

<span data-ttu-id="946b2-152">Последним шагом станет проверка и утверждение предложенных изменений в файлах манифеста и проекта:</span><span class="sxs-lookup"><span data-stu-id="946b2-152">The final step is reviewing and approving the proposed changes to the manifest and project files:</span></span>

* <span data-ttu-id="946b2-153">Слева отображаются предлагаемые изменения в манифесте.</span><span class="sxs-lookup"><span data-stu-id="946b2-153">The proposed changes to the manifest are displayed on the left</span></span>
* <span data-ttu-id="946b2-154">Справа приведены файлы, которые будут добавлены в проект.</span><span class="sxs-lookup"><span data-stu-id="946b2-154">The files to be added to the project are listed to the right</span></span>
* <span data-ttu-id="946b2-155">Кнопка **Compare** (Сравнить) позволяет просматривать в двух соседних окнах текущую версию манифеста и предлагаемые изменения.</span><span class="sxs-lookup"><span data-stu-id="946b2-155">The **Compare** button allows for side by side viewing of the current manifest and the proposed changes</span></span>

![Авторизация](images/FeatureToolApprovalRequest.png)

<span data-ttu-id="946b2-157">Дополнительные сведения см. в статье [Просмотр и утверждение изменений в проекте](reviewing-changes.md).</span><span class="sxs-lookup"><span data-stu-id="946b2-157">For more information, see [reviewing and approving project modifications](reviewing-changes.md).</span></span>

## <a name="5-project-updated"></a><span data-ttu-id="946b2-158">5. Проект обновлен</span><span class="sxs-lookup"><span data-stu-id="946b2-158">5. Project updated</span></span>

<span data-ttu-id="946b2-159">После утверждения предложенных изменений будет обновлен целевой проект Unity, чтобы он содержал ссылки на выбранные функции смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="946b2-159">When the proposed changes are approved, your target Unity project is updated to reference the selected Mixed Reality features:</span></span>

![Проект обновлен](images/FeatureToolProjectUpdated.png)

<span data-ttu-id="946b2-161">В папке **Packages** проекта Unity теперь содержится вложенная папка **MixedReality** с файлами пакетов функций, а манифест будет содержать соответствующие ссылки.</span><span class="sxs-lookup"><span data-stu-id="946b2-161">The Unity project's **Packages** folder now has a **MixedReality** subfolder with the feature package file(s) and the manifest will contain the appropriate reference(s).</span></span>

<span data-ttu-id="946b2-162">Вернитесь в Unity, дождитесь загрузки новых функций и приступайте к разработке.</span><span class="sxs-lookup"><span data-stu-id="946b2-162">Return to Unity, wait for the new selected features to load, and start building!</span></span>

## <a name="see-also"></a><span data-ttu-id="946b2-163">См. также</span><span class="sxs-lookup"><span data-stu-id="946b2-163">See also</span></span>

- [<span data-ttu-id="946b2-164">Настройка средства функций</span><span class="sxs-lookup"><span data-stu-id="946b2-164">Configuring the feature tool</span></span>](configuring-feature-tool.md)
- [<span data-ttu-id="946b2-165">Обнаружение и получение</span><span class="sxs-lookup"><span data-stu-id="946b2-165">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="946b2-166">Просмотр сведений о пакете функций</span><span class="sxs-lookup"><span data-stu-id="946b2-166">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="946b2-167">Импорт выбранных пакетов</span><span class="sxs-lookup"><span data-stu-id="946b2-167">Importing selected packages</span></span>](importing-features.md)
- [<span data-ttu-id="946b2-168">Просмотр и утверждение изменений в проекте</span><span class="sxs-lookup"><span data-stu-id="946b2-168">Reviewing and approving project modifications</span></span>](reviewing-changes.md)
