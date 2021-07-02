---
title: Обновление с предыдущих версий
description: Документация по миграции с более ранней версии МРТК.
author: polar-kev
ms.author: kesemple
ms.date: 04/19/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 5a914d6408d346dac0bf6c683f401564e875f4d8
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175104"
---
# <a name="updating-from-earlier-versions"></a><span data-ttu-id="ebfa9-104">Обновление с предыдущих версий</span><span class="sxs-lookup"><span data-stu-id="ebfa9-104">Updating from earlier versions</span></span>

- [<span data-ttu-id="ebfa9-105">Обновление до новой версии МРТК</span><span class="sxs-lookup"><span data-stu-id="ebfa9-105">Upgrading to a new version of MRTK</span></span>](#upgrading-to-a-new-version-of-mrtk)
- [<span data-ttu-id="ebfa9-106">2.3.0 2.4.0</span><span class="sxs-lookup"><span data-stu-id="ebfa9-106">2.3.0 to 2.4.0</span></span>](#updating-230-to-240)
- [<span data-ttu-id="ebfa9-107">2.2.0 2.3.0</span><span class="sxs-lookup"><span data-stu-id="ebfa9-107">2.2.0 to 2.3.0</span></span>](#updating-220-to-230)
- [<span data-ttu-id="ebfa9-108">2.1.0 2.2.0</span><span class="sxs-lookup"><span data-stu-id="ebfa9-108">2.1.0 to 2.2.0</span></span>](#updating-210-to-220)
- [<span data-ttu-id="ebfa9-109">2.0.0 2.1.0</span><span class="sxs-lookup"><span data-stu-id="ebfa9-109">2.0.0 to 2.1.0</span></span>](#updating-200-to-210)
- [<span data-ttu-id="ebfa9-110">От RC2 до 2.0.0</span><span class="sxs-lookup"><span data-stu-id="ebfa9-110">RC2 to 2.0.0</span></span>](#updating-rc2-to-200)

## <a name="finding-the-current-version"></a><span data-ttu-id="ebfa9-111">Поиск текущей версии</span><span class="sxs-lookup"><span data-stu-id="ebfa9-111">Finding the current version</span></span> 

<span data-ttu-id="ebfa9-112">Чтобы узнать, какая версия МРТК сейчас используется, выполните следующие инструкции:</span><span class="sxs-lookup"><span data-stu-id="ebfa9-112">Follow these instructions to figure out which version of the MRTK you're currently using:</span></span>

1. <span data-ttu-id="ebfa9-113">Открытие проекта МРТК в Unity</span><span class="sxs-lookup"><span data-stu-id="ebfa9-113">Open your MRTK project in Unity</span></span>
2. <span data-ttu-id="ebfa9-114">перейдите в папку "микседреалититулкит" в окне Project</span><span class="sxs-lookup"><span data-stu-id="ebfa9-114">Navigate to the "MixedRealityToolkit" folder in your Project window</span></span>
3. <span data-ttu-id="ebfa9-115">Откройте файл с именем «Version».</span><span class="sxs-lookup"><span data-stu-id="ebfa9-115">Open the file called "Version"</span></span>

<span data-ttu-id="ebfa9-116">Если указанный файл и папка не существуют, вы используете более новую версию МРТК.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-116">If the file and folder above doesn't exist, you're on a newer version of the MRTK.</span></span> <span data-ttu-id="ebfa9-117">В этом случае попробуйте выполнить следующие действия.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-117">In that case, try the following:</span></span>

1. <span data-ttu-id="ebfa9-118">перейдите к папке "Mixed Reality набор средств Foundation"</span><span class="sxs-lookup"><span data-stu-id="ebfa9-118">Navigate to the "Mixed Reality Toolkit Foundation" folder</span></span>
2. <span data-ttu-id="ebfa9-119">Щелкните "package.js", чтобы просмотреть предварительный просмотр в Unity или открыть его в текстовом редакторе.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-119">Click on the "package.json" to see a preview in Unity or open it with a text editor</span></span>
3. <span data-ttu-id="ebfa9-120">Найдите строку со словом Version:</span><span class="sxs-lookup"><span data-stu-id="ebfa9-120">Look for the line with the word "version:"</span></span> 

## <a name="upgrading-to-a-new-version-of-mrtk"></a><span data-ttu-id="ebfa9-121">Обновление до новой версии МРТК</span><span class="sxs-lookup"><span data-stu-id="ebfa9-121">Upgrading to a new version of MRTK</span></span>

<span data-ttu-id="ebfa9-122">*Настоятельно рекомендуется запустить [средство миграции](../features/tools/migration-window.md) после обновления мртк* для автоматического исправления и обновления с устаревших компонентов и настроить на критические изменения.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-122">*It is strongly recommended to run the [migration tool](../features/tools/migration-window.md) after getting the MRTK update* to auto-fix and upgrade from deprecated components and adjust to breaking changes.</span></span> <span data-ttu-id="ebfa9-123">Средство миграции является частью пакета **средств** .</span><span class="sxs-lookup"><span data-stu-id="ebfa9-123">The migration tool is part of the **Tools** package.</span></span>

<span data-ttu-id="ebfa9-124">В приведенных ниже инструкциях описан путь обновления 2.4.0 to 2.5.0.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-124">The instructions below describe the 2.4.0 to 2.5.0 upgrade path.</span></span> <span data-ttu-id="ebfa9-125">Если проект находится в 2.3.0 или более ранней версии, прочтите изменения [между версиями](#updating-230-to-240) , чтобы понять путь обновления, или ознакомьтесь с [инструкциями предыдущего выпуска](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) , чтобы выполнить обновление версий по версии.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-125">If your project is on 2.3.0 or earlier, read on to the changes [between versions](#updating-230-to-240) to understand the upgrade path, or read the previous [release's instructions](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) to do a version-by-version upgrade.</span></span>

### <a name="mixed-reality-feature-tool"></a><span data-ttu-id="ebfa9-126">Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="ebfa9-126">Mixed Reality Feature Tool</span></span>
<span data-ttu-id="ebfa9-127">Самый простой способ обновить МРТК до более новой версии МРТК — использовать [средство "функция смешанной реальности](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) " для загрузки последних пакетов и их загрузки непосредственно в проект Unity.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-127">The easiest way to upgrade MRTK to a newer version MRTK is by using the [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) to download the latest packages and load them directly to your Unity project.</span></span>

<span data-ttu-id="ebfa9-128">Если в проекте ранее использовались файлы ресурсов Unity (. пакет unitypackage), см. [эти инструкции](#switching-from-unity-asset-files-to-mixed-reality-feature-tool).</span><span class="sxs-lookup"><span data-stu-id="ebfa9-128">If the project previously used Unity asset (.unitypackage) files, please see [these instructions](#switching-from-unity-asset-files-to-mixed-reality-feature-tool).</span></span> 

### <a name="unity-asset-unitypackage-files"></a><span data-ttu-id="ebfa9-129">Файлы ресурсов Unity (. пакет unitypackage)</span><span class="sxs-lookup"><span data-stu-id="ebfa9-129">Unity asset (.unitypackage) files</span></span>

<span data-ttu-id="ebfa9-130">Другой способ обновления — вручную загрузить пакеты Unity МРТК и применить их к проекту.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-130">Another upgrade path is to manually download MRTK Unity packages and apply them to your project.</span></span> <span data-ttu-id="ebfa9-131">См. действия ниже.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-131">See the steps below,</span></span>

1. <span data-ttu-id="ebfa9-132">Сохраните копию текущего проекта, если вы достигли любого трудностямиа в любой момент на шагах обновления.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-132">Save a copy of your current project, in case you hit any snags at any point in the upgrade steps.</span></span>
1. <span data-ttu-id="ebfa9-133">Закрыть Unity</span><span class="sxs-lookup"><span data-stu-id="ebfa9-133">Close Unity</span></span>
1. <span data-ttu-id="ebfa9-134">В папке *Assets* удалите следующие папки **мртк** вместе с файлами. meta (проект может иметь не все перечисленные папки).</span><span class="sxs-lookup"><span data-stu-id="ebfa9-134">Inside the *Assets* folder, delete the following **MRTK** folders, along with their .meta files (the project may not have all listed folders)</span></span>
    - <span data-ttu-id="ebfa9-135">МРТК/Core</span><span class="sxs-lookup"><span data-stu-id="ebfa9-135">MRTK/Core</span></span>
    - <span data-ttu-id="ebfa9-136">МРТК/примеры</span><span class="sxs-lookup"><span data-stu-id="ebfa9-136">MRTK/Examples</span></span>
    - <span data-ttu-id="ebfa9-137">МРТК и расширения</span><span class="sxs-lookup"><span data-stu-id="ebfa9-137">MRTK/Extensions</span></span>
    - <span data-ttu-id="ebfa9-138">МРТК и поставщики</span><span class="sxs-lookup"><span data-stu-id="ebfa9-138">MRTK/Providers</span></span>
    - <span data-ttu-id="ebfa9-139">МРТК И ПАКЕТ SDK</span><span class="sxs-lookup"><span data-stu-id="ebfa9-139">MRTK/SDK</span></span>
    - <span data-ttu-id="ebfa9-140">МРТК и службы</span><span class="sxs-lookup"><span data-stu-id="ebfa9-140">MRTK/Services</span></span>
    - <span data-ttu-id="ebfa9-141">МРТК/Стандардассетс</span><span class="sxs-lookup"><span data-stu-id="ebfa9-141">MRTK/StandardAssets</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="ebfa9-142">Если в шейдеры МРТК были внесены изменения, создайте локальную резервную копию перед удалением папки МРТК/Стандардассетс</span><span class="sxs-lookup"><span data-stu-id="ebfa9-142">If modifications were made to the MRTK shaders, create a local backup before deleteing the MRTK/StandardAssets folder</span></span>
    - <span data-ttu-id="ebfa9-143">МРТК и средства</span><span class="sxs-lookup"><span data-stu-id="ebfa9-143">MRTK/Tools</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="ebfa9-144">НЕ удаляйте папку **микседреалититулкит. Generated** или ее мета файл.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-144">Do NOT delete the **MixedRealityToolkit.Generated** folder, or its .meta file.</span></span>
1. <span data-ttu-id="ebfa9-145">Удаление папки **библиотеки**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-145">Delete the **Library** folder</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="ebfa9-146">Некоторые средства Unity, такие как Unity Коллаб, сохраняют сведения о конфигурации в папке Library.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-146">Some Unity tools, like Unity Collab, save configuration info to the Library folder.</span></span> <span data-ttu-id="ebfa9-147">При использовании средства, которое делает это, сначала скопируйте папку с данными этого средства из библиотеки перед удалением, а затем восстановите ее после повторного создания библиотеки.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-147">If using a tool that does this, first copy the tool's data folder from Library before deleting, then restore it after Library is regenerated.</span></span>
1. <span data-ttu-id="ebfa9-148">Повторное открытие проекта в Unity</span><span class="sxs-lookup"><span data-stu-id="ebfa9-148">Re-open the project in Unity</span></span>
1. <span data-ttu-id="ebfa9-149">Импорт новых пакетов Unity</span><span class="sxs-lookup"><span data-stu-id="ebfa9-149">Import the new unity packages</span></span>
    - <span data-ttu-id="ebfa9-150">Foundation — _сначала импортируйте этот пакет_</span><span class="sxs-lookup"><span data-stu-id="ebfa9-150">Foundation - _Import this package first_</span></span>
    - <span data-ttu-id="ebfa9-151">Инструменты</span><span class="sxs-lookup"><span data-stu-id="ebfa9-151">Tools</span></span>
    - <span data-ttu-id="ebfa9-152">Используемых Расширений</span><span class="sxs-lookup"><span data-stu-id="ebfa9-152">(Optional) Extensions</span></span>
    > [!NOTE]
    > <span data-ttu-id="ebfa9-153">Если были установлены дополнительные расширения, их, возможно, потребуется повторно импортировать.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-153">If additional extensions had been installed, they may need to be re-imported.</span></span>
    - <span data-ttu-id="ebfa9-154">Используемых Примеров</span><span class="sxs-lookup"><span data-stu-id="ebfa9-154">(Optional) Examples</span></span>
1. <span data-ttu-id="ebfa9-155">Закройте Unity и удалите папку **библиотеки** (сначала прочитайте примечание ниже).</span><span class="sxs-lookup"><span data-stu-id="ebfa9-155">Close Unity and delete the **Library** folder (read the note below first!).</span></span> <span data-ttu-id="ebfa9-156">Этот шаг необходим для принудительного обновления базы данных активов Unity и согласования существующих настраиваемых профилей.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-156">This step is necessary to force Unity to refresh its asset database and reconcile existing custom profiles.</span></span>
1. <span data-ttu-id="ebfa9-157">Запуск Unity и для каждой сцены в проекте</span><span class="sxs-lookup"><span data-stu-id="ebfa9-157">Launch Unity, and for each scene in the project</span></span>
    - <span data-ttu-id="ebfa9-158">Удалите **микседреалититулкит** и **микседреалитиплайспаце**, если они есть, из иерархии.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-158">Delete **MixedRealityToolkit** and **MixedRealityPlayspace**, if present, from the hierarchy.</span></span> <span data-ttu-id="ebfa9-159">При этом будет удалена основная камера, но она будет создана повторно на следующем шаге.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-159">This will delete the main camera, but it will be re-created in the next step.</span></span> <span data-ttu-id="ebfa9-160">Если какие-либо свойства основной камеры были изменены вручную, их необходимо будет повторно применить вручную после создания новой камеры.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-160">If any properties of the main camera have been manually changed, these will have to be re-applied manually once the new camera is created.</span></span>
    - <span data-ttu-id="ebfa9-161">Выберите **микседреалититулкит-> добавить в сцену и настроить** .</span><span class="sxs-lookup"><span data-stu-id="ebfa9-161">Select **MixedRealityToolkit -> Add to Scene and Configure**</span></span>
    - <span data-ttu-id="ebfa9-162">Выберите **микседреалититулкит-> служебные программы-> профили сопоставления контроллеров >** (только один раз). при этом будут обновлены все пользовательские профили сопоставления контроллеров с обновленными осями и данными, оставляя настраиваемые действия ввода без изменений.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-162">Select **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** (only needs to be done once)       - This will update any custom controller mapping profiles with updated axes and data, while leaving your custom-assigned input actions intact</span></span>
1. <span data-ttu-id="ebfa9-163">запустите [средство миграции](../features/tools/migration-window.md) и запустите средство на *полной Project* , чтобы убедиться, что весь код обновлен до последней версии.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-163">Run the [migration tool](../features/tools/migration-window.md) and run the tool on the *Full Project* to ensure that all of your code is updated to the latest.</span></span>
   <span data-ttu-id="ebfa9-164">Окно миграции содержит ряд различных обработчиков миграции, каждый из которых должен выполняться самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-164">The migration window contains a number of different migration handlers, which must each be run on their own.</span></span> <span data-ttu-id="ebfa9-165">Этот шаг включает в себя следующее:</span><span class="sxs-lookup"><span data-stu-id="ebfa9-165">This step involves:</span></span>
   - <span data-ttu-id="ebfa9-166">Выберите первый обработчик миграции из раскрывающегося списка **Выбор обработчика миграции** .</span><span class="sxs-lookup"><span data-stu-id="ebfa9-166">Select the first migration handler from the **Migration Handler Selection** dropdown.</span></span>
   - <span data-ttu-id="ebfa9-167">нажмите кнопку "полная Project".</span><span class="sxs-lookup"><span data-stu-id="ebfa9-167">Click the "Full Project" button.</span></span>
   - <span data-ttu-id="ebfa9-168">Нажмите кнопку "Добавить полную версию проекта для миграции" (это будет проверять весь проект для переносимых объектов).</span><span class="sxs-lookup"><span data-stu-id="ebfa9-168">Click the "Add full project for migration" button (this will scan the entire project for objects to migrate).</span></span>
   - <span data-ttu-id="ebfa9-169">Нажмите кнопку "миграция", которая должна быть включена при обнаружении любых переносимых объектов.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-169">Click the "Migrate" button which should be enabled if any migrateable objects were found.</span></span>
   - <span data-ttu-id="ebfa9-170">Повторите предыдущие три шага для каждого из обработчиков миграции в раскрывающемся списке.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-170">Repeat the previous three steps for each of the migration handlers within the dropdown.</span></span>
     <span data-ttu-id="ebfa9-171">(Ознакомьтесь с [этой проблемой](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) , которая охватывает работу, которую можно сделать для упрощения процесса миграции в будущем выпуске).</span><span class="sxs-lookup"><span data-stu-id="ebfa9-171">(See [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) which covers work that can be done to simplify this migration process in a future release)</span></span>

### <a name="switching-from-unity-asset-files-to-mixed-reality-feature-tool"></a><span data-ttu-id="ebfa9-172">Переключение из файлов ресурсов Unity в инструмент для функций смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="ebfa9-172">Switching from Unity asset files to Mixed Reality Feature Tool</span></span>

<span data-ttu-id="ebfa9-173">Переключение из файлов ресурсов Unity в пакеты средств смешанной реальности предоставляет ряд преимуществ.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-173">Switching from Unity asset files to Mixed Reality Feature Tool packages brings a number of benefits:</span></span>

- <span data-ttu-id="ebfa9-174">Упрощенное обновление</span><span class="sxs-lookup"><span data-stu-id="ebfa9-174">Easier updating</span></span>
- <span data-ttu-id="ebfa9-175">Более быстрое время компиляции</span><span class="sxs-lookup"><span data-stu-id="ebfa9-175">Faster compile times</span></span>
- <span data-ttu-id="ebfa9-176">меньше проектов в Visual Studio решении</span><span class="sxs-lookup"><span data-stu-id="ebfa9-176">Fewer projects in the Visual Studio solution</span></span>

<span data-ttu-id="ebfa9-177">Переход на использование средства "функция смешанной реальности" требует однократного выполнения ручных действий.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-177">Changing to using the Mixed Reality Feature Tool requires a one-time set of manual steps.</span></span>

1. <span data-ttu-id="ebfa9-178">Сохраните копию текущего проекта.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-178">Save a copy of your current project.</span></span>
1. <span data-ttu-id="ebfa9-179">Закрыть Unity</span><span class="sxs-lookup"><span data-stu-id="ebfa9-179">Close Unity</span></span>
1. <span data-ttu-id="ebfa9-180">В папке *Assets* удалите следующие папки **мртк** вместе с файлами. meta (проект может иметь не все перечисленные папки).</span><span class="sxs-lookup"><span data-stu-id="ebfa9-180">Inside the *Assets* folder, delete the following **MRTK** folders, along with their .meta files (the project may not have all listed folders)</span></span>
    - <span data-ttu-id="ebfa9-181">МРТК/Core</span><span class="sxs-lookup"><span data-stu-id="ebfa9-181">MRTK/Core</span></span>
    - <span data-ttu-id="ebfa9-182">МРТК/примеры</span><span class="sxs-lookup"><span data-stu-id="ebfa9-182">MRTK/Examples</span></span>
    - <span data-ttu-id="ebfa9-183">МРТК и расширения</span><span class="sxs-lookup"><span data-stu-id="ebfa9-183">MRTK/Extensions</span></span>
    - <span data-ttu-id="ebfa9-184">МРТК и поставщики</span><span class="sxs-lookup"><span data-stu-id="ebfa9-184">MRTK/Providers</span></span>
    - <span data-ttu-id="ebfa9-185">МРТК И ПАКЕТ SDK</span><span class="sxs-lookup"><span data-stu-id="ebfa9-185">MRTK/SDK</span></span>
    - <span data-ttu-id="ebfa9-186">МРТК и службы</span><span class="sxs-lookup"><span data-stu-id="ebfa9-186">MRTK/Services</span></span>
    - <span data-ttu-id="ebfa9-187">МРТК/Стандардассетс</span><span class="sxs-lookup"><span data-stu-id="ebfa9-187">MRTK/StandardAssets</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="ebfa9-188">Если в шейдеры МРТК были внесены изменения, создайте локальную резервную копию перед удалением папки МРТК/Стандардассетс</span><span class="sxs-lookup"><span data-stu-id="ebfa9-188">If modifications were made to the MRTK shaders, create a local backup before deleteing the MRTK/StandardAssets folder</span></span>
    - <span data-ttu-id="ebfa9-189">МРТК и средства</span><span class="sxs-lookup"><span data-stu-id="ebfa9-189">MRTK/Tools</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="ebfa9-190">НЕ удаляйте папку **микседреалититулкит. Generated** или ее мета файл.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-190">Do NOT delete the **MixedRealityToolkit.Generated** folder, or its .meta file.</span></span>
1. <span data-ttu-id="ebfa9-191">Удаление папки **библиотеки**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-191">Delete the **Library** folder</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="ebfa9-192">Некоторые средства Unity, такие как Unity Коллаб, сохраняют сведения о конфигурации в папке Library.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-192">Some Unity tools, like Unity Collab, save configuration info to the Library folder.</span></span> <span data-ttu-id="ebfa9-193">При использовании средства, которое делает это, сначала скопируйте папку с данными этого средства из библиотеки перед удалением, а затем восстановите ее после повторного создания библиотеки.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-193">If using a tool that does this, first copy the tool's data folder from Library before deleting, then restore it after Library is regenerated.</span></span>
1. <span data-ttu-id="ebfa9-194">Повторное открытие проекта в Unity</span><span class="sxs-lookup"><span data-stu-id="ebfa9-194">Re-open the project in Unity</span></span>

<span data-ttu-id="ebfa9-195">после выполнения предыдущих действий запустите [средство "функция смешанной реальности](#mixed-reality-feature-tool) " и импортируйте нужную версию набор средств смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-195">Once the previous steps have been performed, run the [Mixed Reality Feature Tool](#mixed-reality-feature-tool) and import the desired version of the Mixed Reality Toolkit.</span></span>

## <a name="updating-230-to-240"></a><span data-ttu-id="ebfa9-196">Обновление 2.3.0 до 2.4.0</span><span class="sxs-lookup"><span data-stu-id="ebfa9-196">Updating 2.3.0 to 2.4.0</span></span>

<span data-ttu-id="ebfa9-197">[Переименование папок](#folder-renames-in-240) 
 [Изменения API](#api-changes-in-240)</span><span class="sxs-lookup"><span data-stu-id="ebfa9-197">[Folder renames](#folder-renames-in-240)
[API changes](#api-changes-in-240)</span></span>

### <a name="folder-renames-in-240"></a><span data-ttu-id="ebfa9-198">Переименование папок в 2.4.0</span><span class="sxs-lookup"><span data-stu-id="ebfa9-198">Folder renames in 2.4.0</span></span>

<span data-ttu-id="ebfa9-199">Папки Микседреалититулкит были переименованы и перемещены в общую иерархию в версии 2,4.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-199">The MixedRealityToolkit folders have been renamed and moved into a common hierarchy in version 2.4.</span></span> <span data-ttu-id="ebfa9-200">Если приложение использует жестко закодированные пути для МРТК ресурсов, их необходимо обновить в соответствии со следующей таблицей.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-200">If an application uses hard coded paths to MRTK resources, they will need to be updated per the following table.</span></span>

| <span data-ttu-id="ebfa9-201">Предыдущая папка</span><span class="sxs-lookup"><span data-stu-id="ebfa9-201">Previous Folder</span></span> | <span data-ttu-id="ebfa9-202">Создать папку</span><span class="sxs-lookup"><span data-stu-id="ebfa9-202">New Folder</span></span> |
| --- | --- |
| <span data-ttu-id="ebfa9-203">MixedRealityToolkit;</span><span class="sxs-lookup"><span data-stu-id="ebfa9-203">MixedRealityToolkit</span></span> | <span data-ttu-id="ebfa9-204">МРТК/Core</span><span class="sxs-lookup"><span data-stu-id="ebfa9-204">MRTK/Core</span></span> |
| <span data-ttu-id="ebfa9-205">Микседреалититулкит. примеры</span><span class="sxs-lookup"><span data-stu-id="ebfa9-205">MixedRealityToolkit.Examples</span></span> | <span data-ttu-id="ebfa9-206">МРТК/примеры</span><span class="sxs-lookup"><span data-stu-id="ebfa9-206">MRTK/Examples</span></span> |
| <span data-ttu-id="ebfa9-207">Микседреалититулкит. Extensions</span><span class="sxs-lookup"><span data-stu-id="ebfa9-207">MixedRealityToolkit.Extensions</span></span> | <span data-ttu-id="ebfa9-208">МРТК и расширения</span><span class="sxs-lookup"><span data-stu-id="ebfa9-208">MRTK/Extensions</span></span> |
| <span data-ttu-id="ebfa9-209">Микседреалититулкит. Providers</span><span class="sxs-lookup"><span data-stu-id="ebfa9-209">MixedRealityToolkit.Providers</span></span> | <span data-ttu-id="ebfa9-210">МРТК и поставщики</span><span class="sxs-lookup"><span data-stu-id="ebfa9-210">MRTK/Providers</span></span> |
| <span data-ttu-id="ebfa9-211">Микседреалититулкит. SDK</span><span class="sxs-lookup"><span data-stu-id="ebfa9-211">MixedRealityToolkit.SDK</span></span> | <span data-ttu-id="ebfa9-212">МРТК И ПАКЕТ SDK</span><span class="sxs-lookup"><span data-stu-id="ebfa9-212">MRTK/SDK</span></span> |
| <span data-ttu-id="ebfa9-213">Микседреалититулкит. Services</span><span class="sxs-lookup"><span data-stu-id="ebfa9-213">MixedRealityToolkit.Services</span></span> | <span data-ttu-id="ebfa9-214">МРТК и службы</span><span class="sxs-lookup"><span data-stu-id="ebfa9-214">MRTK/Services</span></span> |
| <span data-ttu-id="ebfa9-215">Микседреалититулкит. Tests</span><span class="sxs-lookup"><span data-stu-id="ebfa9-215">MixedRealityToolkit.Tests</span></span> | <span data-ttu-id="ebfa9-216">МРТК и тесты</span><span class="sxs-lookup"><span data-stu-id="ebfa9-216">MRTK/Tests</span></span> |
| <span data-ttu-id="ebfa9-217">Микседреалититулкит. Tools</span><span class="sxs-lookup"><span data-stu-id="ebfa9-217">MixedRealityToolkit.Tools</span></span> | <span data-ttu-id="ebfa9-218">МРТК и средства</span><span class="sxs-lookup"><span data-stu-id="ebfa9-218">MRTK/Tools</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="ebfa9-219">`MixedRealityToolkit.Generated`Содержит файлы, созданные клиентом, и остается без изменений.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-219">The `MixedRealityToolkit.Generated` contains customer generated files and remains unchanged.</span></span>

### <a name="eye-gaze-setup-in-240"></a><span data-ttu-id="ebfa9-220">Установка взгляда на глаза в 2.4.0</span><span class="sxs-lookup"><span data-stu-id="ebfa9-220">Eye gaze setup in 2.4.0</span></span>

<span data-ttu-id="ebfa9-221">Эта версия МРТК изменяет шаги, необходимые для установки взгляда на глаза.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-221">This version of MRTK modifies the steps required for eye gaze setup.</span></span> <span data-ttu-id="ebfa9-222">Флажок _"исэйетраккинженаблед"_ можно найти в параметрах взгляда профиля входного указателя.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-222">The _'IsEyeTrackingEnabled'_ checkbox can be found in the gaze settings of the input pointer profile.</span></span> <span data-ttu-id="ebfa9-223">Установка этого флажка включает взгляд на глаза, а не на заголовку по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-223">Checking this box will enable eye based gaze, rather then the default head based gaze.</span></span>

<span data-ttu-id="ebfa9-224">Дополнительные сведения об этих изменениях и полные инструкции по настройке отслеживания взгляда см. в статье [Отслеживание отслеживания взглядов](../features/input/eye-tracking/eye-tracking-basic-setup.md) .</span><span class="sxs-lookup"><span data-stu-id="ebfa9-224">For more information on these changes and complete instructions for eye tracking setup, please see the [eye tracking](../features/input/eye-tracking/eye-tracking-basic-setup.md) article.</span></span>

### <a name="eye-gaze-pointer-behavior-in-240"></a><span data-ttu-id="ebfa9-225">Поведение указателя взгляда на глаз в 2.4.0</span><span class="sxs-lookup"><span data-stu-id="ebfa9-225">Eye gaze pointer behavior in 2.4.0</span></span>

<span data-ttu-id="ebfa9-226">Вид указателя по умолчанию был изменен в соответствии с поведением указателя по умолчанию для основного взгляда.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-226">The eye gaze default pointer behavior have been modified to match the head gaze default pointer behavior.</span></span> <span data-ttu-id="ebfa9-227">Указатель взгляда на глаз будет автоматически подавлен после обнаружения руки.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-227">An eye gaze pointer will automatically be suppressed once a hand is detected.</span></span> <span data-ttu-id="ebfa9-228">После произнесения слова "Select" указатель глаза становится видимым снова.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-228">The eye gaze pointer will become visible again after saying "Select".</span></span>

<span data-ttu-id="ebfa9-229">Сведения о настройках взгляда и руки можно найти в статье [глаза и руки](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) .</span><span class="sxs-lookup"><span data-stu-id="ebfa9-229">Details about gaze and hand setups can be found in the [eyes and hands](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) article.</span></span>

### <a name="api-changes-in-240"></a><span data-ttu-id="ebfa9-230">Изменения API в 2.4.0</span><span class="sxs-lookup"><span data-stu-id="ebfa9-230">API changes in 2.4.0</span></span>

<span data-ttu-id="ebfa9-231">**Классы пользовательских контроллеров**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-231">**Custom controller classes**</span></span>

<span data-ttu-id="ebfa9-232">Классы пользовательских контроллеров ранее были определены `SetupDefaultInteractions(Handedness)` .</span><span class="sxs-lookup"><span data-stu-id="ebfa9-232">Custom controller classes previously had to define `SetupDefaultInteractions(Handedness)`.</span></span> <span data-ttu-id="ebfa9-233">Этот метод был устаревшим в 2,4, так как параметр правой или левой был избыточен с помощью класса контроллера правой или левой.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-233">This method has been made obsolete in 2.4, as the handedness parameter was redundant with the controller class' own handedness.</span></span> <span data-ttu-id="ebfa9-234">Новый метод не имеет параметров.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-234">The new method has no parameters.</span></span> <span data-ttu-id="ebfa9-235">Кроме того, многие классы контроллеров определены таким же образом ( `AssignControllerMappings(DefaultInteractions);` ), поэтому полный вызов был `BaseController` выполнен рефакторинг и сделан необязательным переопределением, а не обязательно.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-235">Additionally, many controller classes defined this the same way (`AssignControllerMappings(DefaultInteractions);`), so the full call has been refactored down into `BaseController` and made an optional override instead of required.</span></span>

<span data-ttu-id="ebfa9-236">**Свойства взгляда на глаз**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-236">**Eye Gaze properties**</span></span>

<span data-ttu-id="ebfa9-237">`UseEyeTracking`Свойство из `GazeProvider` реализации `IMixedRealityEyeGazeProvider` было переименовано в `IsEyeTrackingEnabled` .</span><span class="sxs-lookup"><span data-stu-id="ebfa9-237">The `UseEyeTracking` property from `GazeProvider` implementation of `IMixedRealityEyeGazeProvider` was renamed to `IsEyeTrackingEnabled`.</span></span>

<span data-ttu-id="ebfa9-238">Если вы сделали это ранее...</span><span class="sxs-lookup"><span data-stu-id="ebfa9-238">If you did this previously...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.UseEyeTracking = true;
}
```

<span data-ttu-id="ebfa9-239">Сделать это сейчас...</span><span class="sxs-lookup"><span data-stu-id="ebfa9-239">Do this now...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.IsEyeTrackingEnabled = true;
}
```

<span data-ttu-id="ebfa9-240">**Свойства Виндовсапичеккер**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-240">**WindowsApiChecker properties**</span></span>

<span data-ttu-id="ebfa9-241">Следующие свойства Виндовсапичеккер помечены как устаревшие.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-241">The following WindowsApiChecker properties have been marked as obsolete.</span></span> <span data-ttu-id="ebfa9-242">Используйте `IsMethodAvailable` `IsPropertyAvailable` или `IsTypeAvailable` .</span><span class="sxs-lookup"><span data-stu-id="ebfa9-242">Please use `IsMethodAvailable`, `IsPropertyAvailable` or `IsTypeAvailable`.</span></span>

- <span data-ttu-id="ebfa9-243">UniversalApiContractV8_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="ebfa9-243">UniversalApiContractV8_IsAvailable</span></span>
- <span data-ttu-id="ebfa9-244">UniversalApiContractV7_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="ebfa9-244">UniversalApiContractV7_IsAvailable</span></span>
- <span data-ttu-id="ebfa9-245">UniversalApiContractV6_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="ebfa9-245">UniversalApiContractV6_IsAvailable</span></span>
- <span data-ttu-id="ebfa9-246">UniversalApiContractV5_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="ebfa9-246">UniversalApiContractV5_IsAvailable</span></span>
- <span data-ttu-id="ebfa9-247">UniversalApiContractV4_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="ebfa9-247">UniversalApiContractV4_IsAvailable</span></span>
- <span data-ttu-id="ebfa9-248">UniversalApiContractV3_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="ebfa9-248">UniversalApiContractV3_IsAvailable</span></span>

<span data-ttu-id="ebfa9-249">Нет планов по добавлению свойств в Виндовсапичеккер для будущих версий контракта API.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-249">There are no plans to add properties to WindowsApiChecker for future API contract versions.</span></span>

<span data-ttu-id="ebfa9-250">**Глтфмешпримитивеаттрибутес только для чтения**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-250">**GltfMeshPrimitiveAttributes read-only**</span></span>

<span data-ttu-id="ebfa9-251">Атрибуты-примитивы сетки глтф, используемые для устанавливаемых параметров, теперь доступны только для чтения.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-251">The gltf mesh primitive attributes used to be settable, they are now read-only.</span></span> <span data-ttu-id="ebfa9-252">Их значения будут заданы один раз при десериализации.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-252">Their values will be set once when deserialized.</span></span>

### <a name="custom-button-icon-migration"></a><span data-ttu-id="ebfa9-253">Миграция значка настраиваемой кнопки</span><span class="sxs-lookup"><span data-stu-id="ebfa9-253">Custom Button Icon Migration</span></span>

<span data-ttu-id="ebfa9-254">Ранее настроенные значки кнопок требуют назначения нового материала для средства визуализации с четырьмя кнопками.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-254">Previously custom button icons required assigning a new material to the button's quad renderer.</span></span> <span data-ttu-id="ebfa9-255">Это больше не требуется, поэтому мы рекомендуем переместить текстуры настраиваемых значков в виде значков.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-255">This is no longer necessary and we recommend moving custom icon textures into an IconSet.</span></span> <span data-ttu-id="ebfa9-256">Существующие пользовательские материалы и значки сохраняются.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-256">Existing custom materials and icons are preserved.</span></span> <span data-ttu-id="ebfa9-257">Однако они будут менее оптимальными до обновления.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-257">However they will be less optimal until upgraded.</span></span>
<span data-ttu-id="ebfa9-258">Чтобы обновить ресурсы на всех кнопках в проекте до нового рекомендуемого формата, используйте Буттонконфигхелпермигратионхандлер.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-258">To upgrade the assets on all buttons in the project to the new recommended format, use the ButtonConfigHelperMigrationHandler.</span></span>
<span data-ttu-id="ebfa9-259">(набор средств, > служебные программы — > окно миграции — > выбор обработчика миграции — > Microsoft. микседреалити. набор средств. Utilities. Буттонконфигхелпермигратионхандлер)</span><span class="sxs-lookup"><span data-stu-id="ebfa9-259">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span></span>

![Диалоговое окно обновления](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

<span data-ttu-id="ebfa9-261">Если значок не найден в наборе значков по умолчанию во время миграции, в Микседреалититулкит. Generated/Кустомиконсетс будет создан пользовательский набор значков.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-261">If an icon is not found in the default icon set during migration, a custom icon set will be created in MixedRealityToolkit.Generated/CustomIconSets.</span></span> <span data-ttu-id="ebfa9-262">В диалоговом окне будет указано, что выполнено.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-262">A dialog will indicate that this has taken place.</span></span>

![Уведомление о настраиваемом значке](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

## <a name="updating-220-to-230"></a><span data-ttu-id="ebfa9-264">Обновление 2.2.0 до 2.3.0</span><span class="sxs-lookup"><span data-stu-id="ebfa9-264">Updating 2.2.0 to 2.3.0</span></span>

- <span data-ttu-id="ebfa9-265">[изменения API](#api-changes-in-230);</span><span class="sxs-lookup"><span data-stu-id="ebfa9-265">[API changes](#api-changes-in-230)</span></span>

### <a name="api-changes-in-230"></a><span data-ttu-id="ebfa9-266">Изменения API в 2.3.0</span><span class="sxs-lookup"><span data-stu-id="ebfa9-266">API changes in 2.3.0</span></span>

<span data-ttu-id="ebfa9-267">**контроллерпосесинчронизер**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-267">**ControllerPoseSynchronizer**</span></span>

<span data-ttu-id="ebfa9-268">Закрытое поле Контроллерпосесинчронизер. правой или левой помечено как устаревшее.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-268">The private ControllerPoseSynchronizer.handedness field has been marked as obsolete.</span></span> <span data-ttu-id="ebfa9-269">Это должно оказать минимальное воздействие на приложения, так как поле не видимо за пределами его класса.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-269">This should have minimal impact on applications as the field is not visible outside of its class.</span></span>

<span data-ttu-id="ebfa9-270">Метод задания свойства public Контроллерпосесинчронизер. правой или левой был удален ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).</span><span class="sxs-lookup"><span data-stu-id="ebfa9-270">The public ControllerPoseSynchronizer.Handedness property's setter has been removed ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).</span></span>

<span data-ttu-id="ebfa9-271">**MSBuild для Unity**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-271">**MSBuild for Unity**</span></span>

<span data-ttu-id="ebfa9-272">эта версия мртк использует более новую версию MSBuild для Unity, чем предыдущие выпуски.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-272">This version of MRTK uses a newer version of MSBuild for Unity than previous releases.</span></span> <span data-ttu-id="ebfa9-273">если при загрузке проекта в манифесте диспетчера пакетов Unity указана более старая версия, появится диалоговое окно настройки с установленным флажком включить MSBuild для Unity.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-273">During project load, if the older version is listed in the Unity Package Manger manifest, the configuration dialog will appear, with the Enable MSBuild for Unity option checked.</span></span> <span data-ttu-id="ebfa9-274">При применении будет выполнено обновление.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-274">Applying will perform an upgrade.</span></span>

<span data-ttu-id="ebfa9-275">**скриптингутилитиес**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-275">**ScriptingUtilities**</span></span>

<span data-ttu-id="ebfa9-276">Класс Скриптингутилитиес был помечен как устаревший и был заменен Скриптутилитиес в Microsoft. Микседреалити. набор средств. Сборка редактора. Utilities.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-276">The ScriptingUtilities class has been marked as obsolete and has been replaced by ScriptUtilities, in the Microsoft.MixedReality.Toolkit.Editor.Utilities assembly.</span></span> <span data-ttu-id="ebfa9-277">Новый класс расширяет предыдущее поведение и добавляет поддержку для удаления определений скриптов.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-277">The new class refines previous behavior and adds support for removing scripting definitions.</span></span>

<span data-ttu-id="ebfa9-278">Несмотря на то, что существующий код будет продолжать работать в версии 2.3.0, рекомендуется обновить его до нового класса.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-278">While existing code will continue to function in version 2.3.0, it is recommended to update to the new class.</span></span>

<span data-ttu-id="ebfa9-279">**шеллхандрайпоинтер**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-279">**ShellHandRayPointer**</span></span>

<span data-ttu-id="ebfa9-280">Члены Линерендерерселектед и Линерендерернотаржет класса Шеллхандрайпоинтер были заменены Линематериалселектед и lineMaterialNoTarget соответственно ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).</span><span class="sxs-lookup"><span data-stu-id="ebfa9-280">The lineRendererSelected and lineRendererNoTarget members of the ShellHandRayPointer class have been replaced by lineMaterialSelected and lineMaterialNoTarget, respectively ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).</span></span>

<span data-ttu-id="ebfa9-281">Замените Линерендерерселектед на Линематериалселектед и/или Линерендерернотаржет на Линематериалнотаржет для разрешения ошибок компиляции.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-281">Please replace lineRendererSelected with lineMaterialSelected and/or lineRendererNoTarget with lineMaterialNoTarget to resolve compile errors.</span></span>

<span data-ttu-id="ebfa9-282">**StartupBehavior пространственного наблюдателя**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-282">**Spatial observer StartupBehavior**</span></span>

<span data-ttu-id="ebfa9-283">Пространственные наблюдатели, созданные на основе `BaseSpatialObserver` класса, теперь соблюдают значение StartupBehavior при повторном включении ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).</span><span class="sxs-lookup"><span data-stu-id="ebfa9-283">Spatial observers built upon the `BaseSpatialObserver` class now honor the value of StartupBehavior when re-enabled ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).</span></span>

<span data-ttu-id="ebfa9-284">Чтобы воспользоваться этим исправлением, никаких изменений не требуется.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-284">No changes are required to take advantage of this fix.</span></span>

<span data-ttu-id="ebfa9-285">**Элемент управления UX Prefabs обновлен для использования Прессаблебуттон**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-285">**UX control prefabs updated to use PressableButton**</span></span>

<span data-ttu-id="ebfa9-286">Следующие Prefabs теперь используют компонент Прессаблебуттон вместо Таучхандлер для NEAR взаимодействия ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))</span><span class="sxs-lookup"><span data-stu-id="ebfa9-286">The following prefabs are now using the PressableButton component instead of TouchHandler for near interaction ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))</span></span>

- <span data-ttu-id="ebfa9-287">аниматионбуттон</span><span class="sxs-lookup"><span data-stu-id="ebfa9-287">AnimationButton</span></span>
- <span data-ttu-id="ebfa9-288">Кнопка</span><span class="sxs-lookup"><span data-stu-id="ebfa9-288">Button</span></span>
- <span data-ttu-id="ebfa9-289">ButtonHoloLens1</span><span class="sxs-lookup"><span data-stu-id="ebfa9-289">ButtonHoloLens1</span></span>
- <span data-ttu-id="ebfa9-290">ButtonHoloLens1Toggle</span><span class="sxs-lookup"><span data-stu-id="ebfa9-290">ButtonHoloLens1Toggle</span></span>
- <span data-ttu-id="ebfa9-291">CheckBox</span><span class="sxs-lookup"><span data-stu-id="ebfa9-291">CheckBox</span></span>
- <span data-ttu-id="ebfa9-292">Радиальный</span><span class="sxs-lookup"><span data-stu-id="ebfa9-292">RadialSet</span></span>
- <span data-ttu-id="ebfa9-293">ToggleButton</span><span class="sxs-lookup"><span data-stu-id="ebfa9-293">ToggleButton</span></span>
- <span data-ttu-id="ebfa9-294">ToggleSwitch</span><span class="sxs-lookup"><span data-stu-id="ebfa9-294">ToggleSwitch</span></span>
- <span data-ttu-id="ebfa9-295">унитюибуттон</span><span class="sxs-lookup"><span data-stu-id="ebfa9-295">UnityUIButton</span></span>
- <span data-ttu-id="ebfa9-296">унитюичеккбоксбуттон</span><span class="sxs-lookup"><span data-stu-id="ebfa9-296">UnityUICheckboxButton</span></span>
- <span data-ttu-id="ebfa9-297">унитюирадиалбуттон</span><span class="sxs-lookup"><span data-stu-id="ebfa9-297">UnityUIRadialButton</span></span>
- <span data-ttu-id="ebfa9-298">унитюитогглебуттон</span><span class="sxs-lookup"><span data-stu-id="ebfa9-298">UnityUIToggleButton</span></span>

<span data-ttu-id="ebfa9-299">Код приложения может потребовать обновления из-за этого изменения.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-299">Application code may require updating due to this change.</span></span>

<span data-ttu-id="ebfa9-300">**Пространство имен Виндовсмикседреалитютилитиес**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-300">**WindowsMixedRealityUtilities namespace**</span></span>

<span data-ttu-id="ebfa9-301">Пространство имен Виндовсмикседреалитютилитиес изменилось с Microsoft. Микседреалити. набор средств. Виндовсмикседреалити. input в Microsoft. Микседреалити. набор средств. Виндовсмикседреалити ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).</span><span class="sxs-lookup"><span data-stu-id="ebfa9-301">The namespace of WindowsMixedRealityUtilities changed from Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input to Microsoft.MixedReality.Toolkit.WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).</span></span>

<span data-ttu-id="ebfa9-302">Обновите инструкции #using, чтобы устранить ошибки компиляции.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-302">Please update #using statements to resolve compile errors.</span></span>

## <a name="updating-210-to-220"></a><span data-ttu-id="ebfa9-303">Обновление 2.1.0 до 2.2.0</span><span class="sxs-lookup"><span data-stu-id="ebfa9-303">Updating 2.1.0 to 2.2.0</span></span>

- <span data-ttu-id="ebfa9-304">[изменения API](#api-changes-in-220);</span><span class="sxs-lookup"><span data-stu-id="ebfa9-304">[API changes](#api-changes-in-220)</span></span>

### <a name="api-changes-in-220"></a><span data-ttu-id="ebfa9-305">Изменения API в 2.2.0</span><span class="sxs-lookup"><span data-stu-id="ebfa9-305">API changes in 2.2.0</span></span>

<span data-ttu-id="ebfa9-306">**Имикседреалитибаундарисистем. Contains**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-306">**IMixedRealityBoundarySystem.Contains**</span></span>

<span data-ttu-id="ebfa9-307">Этот метод ранее использовался в определенном экспериментальном перечислении, определенном Unity.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-307">This method previously took in a specific, Unity-defined experimental enum.</span></span> <span data-ttu-id="ebfa9-308">Теперь он принимает определяемое МРТК перечисление, идентичное перечислению Unity.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-308">It now takes in an MRTK-defined enum that's identical to the Unity enum.</span></span> <span data-ttu-id="ebfa9-309">Это изменение помогает подготовить МРТК для будущих API границ Unity.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-309">This change helps prepare the MRTK for Unity's future boundary APIs.</span></span>

<span data-ttu-id="ebfa9-310">**микседреалитисервицепрофилеаттрибуте**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-310">**MixedRealityServiceProfileAttribute**</span></span>

<span data-ttu-id="ebfa9-311">Чтобы лучше описать требования для поддержки профиля, Микседреалитисервицепрофилеаттрибуте был обновлен для добавления необязательной коллекции исключенных типов.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-311">To better describe the requirements for supporting a profile, the MixedRealityServiceProfileAttribute has been updated to add an optional collection of excluded types.</span></span> <span data-ttu-id="ebfa9-312">В рамках этого изменения свойство ServiceType было изменено с Type на Type [] и было переименовано в Рекуиредтипес.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-312">As part of this change, the ServiceType property has been changed from Type to Type[] and been renamed to RequiredTypes.</span></span>

<span data-ttu-id="ebfa9-313">Также было добавлено второе свойство Ексклудедтипес.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-313">A second property, ExcludedTypes has also been added.</span></span>

## <a name="updating-200-to-210"></a><span data-ttu-id="ebfa9-314">Обновление 2.0.0 до 2.1.0</span><span class="sxs-lookup"><span data-stu-id="ebfa9-314">Updating 2.0.0 to 2.1.0</span></span>

- <span data-ttu-id="ebfa9-315">[изменения API](#api-changes-in-210);</span><span class="sxs-lookup"><span data-stu-id="ebfa9-315">[API changes](#api-changes-in-210)</span></span>
- [<span data-ttu-id="ebfa9-316">Изменения профиля</span><span class="sxs-lookup"><span data-stu-id="ebfa9-316">Profile changes</span></span>](#profile-changes-in-210)

### <a name="api-changes-in-210"></a><span data-ttu-id="ebfa9-317">Изменения API в 2.1.0</span><span class="sxs-lookup"><span data-stu-id="ebfa9-317">API changes in 2.1.0</span></span>

<span data-ttu-id="ebfa9-318">**басенеаринтерактионтаучабле**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-318">**BaseNearInteractionTouchable**</span></span>

<span data-ttu-id="ebfa9-319">Был `BaseNearInteractionTouchable` изменен, чтобы пометить `OnValidate` метод как виртуальный.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-319">The `BaseNearInteractionTouchable` has been modified to mark the `OnValidate` method as virtual.</span></span> <span data-ttu-id="ebfa9-320">Классы, расширяющие `BaseNearInteractionTouchable` (например `NearInteractionTouchableUnityUI` ,), были обновлены, чтобы отразить это изменение.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-320">Classes that extend `BaseNearInteractionTouchable` (ex: `NearInteractionTouchableUnityUI`) have been updated to reflect this change.</span></span>

<span data-ttu-id="ebfa9-321">**коллидернеаринтерактионтаучабле**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-321">**ColliderNearInteractionTouchable**</span></span>

<span data-ttu-id="ebfa9-322">Класс `ColliderNearInteractionTouchable` не рекомендуется к использованию.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-322">The `ColliderNearInteractionTouchable` class has been deprecated.</span></span> <span data-ttu-id="ebfa9-323">Обновите ссылки на код для использования `BaseNearInteractionTouchable` .</span><span class="sxs-lookup"><span data-stu-id="ebfa9-323">Please update code references to use `BaseNearInteractionTouchable`.</span></span>

<span data-ttu-id="ebfa9-324">**имикседреалитимауседевицеманажер**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-324">**IMixedRealityMouseDeviceManager**</span></span>

<span data-ttu-id="ebfa9-325">**_Добавлено_**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-325">**_Added_**</span></span>

<span data-ttu-id="ebfa9-326">`IMixedRealityMouseDeviceManager` были добавлены `CursorSpeed` Свойства и `WheelSpeed` .</span><span class="sxs-lookup"><span data-stu-id="ebfa9-326">`IMixedRealityMouseDeviceManager` has been added `CursorSpeed` and `WheelSpeed` properties.</span></span> <span data-ttu-id="ebfa9-327">Эти свойства позволяют приложениям указать значение множителя, на которое будут масштабироваться скорость курсора и колесика соответственно.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-327">These properties allow applications to specify a multiplier value by which the speed of the cursor and wheel, respectively will be scaled.</span></span>

<span data-ttu-id="ebfa9-328">Это критическое изменение, требующее изменения существующих реализаций диспетчера устройств мыши.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-328">This is a breaking change and requires existing mouse device manager implementations to be modified .</span></span>

>[!NOTE]
><span data-ttu-id="ebfa9-329">Это изменение не обратно совместимо с версией 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-329">This change is not backwards compatible with version 2.0.0.</span></span>

<span data-ttu-id="ebfa9-330">**_Не рекомендуется_**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-330">**_Deprecated_**</span></span>

<span data-ttu-id="ebfa9-331">`MouseInputProfile`свойство помечено как устаревшее и будет удалено из будущей версии набор средств Microsoft Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-331">The `MouseInputProfile` property has been marked as obsolete and will be removed from a future version of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="ebfa9-332">Рекомендуется, чтобы код приложения больше не использовал это свойство.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-332">It is recommended that application code no longer use this property.</span></span>

<span data-ttu-id="ebfa9-333">**Интерактивный объект**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-333">**Interactable**</span></span>

<span data-ttu-id="ebfa9-334">следующие методы и свойства являются устаревшими и будут удалены из будущей версии набор средств Microsoft Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-334">The following methods and properties have been deprecated and will be removed from a future version of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="ebfa9-335">Рекомендуется обновлять код приложения в соответствии с рекомендациями, содержащимися в атрибуте obsolete и отображаемых в консоли.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-335">The recommendation is to update application code per the guidance contained in the Obsolete attribute and displayed in the console.</span></span>

- `public bool Enabled`
- `public bool FocusEnabled`
- `public void ForceUpdateThemes()`
- `public bool IsDisabled`
- `public bool IsToggleButton`
- `public int GetDimensionIndex()`
- `public State[] GetStates()`
- `public bool RequiresFocus`
- `public void ResetBaseStates()`
- `public virtual void SetCollision(bool collision)`
- `public virtual void SetCustom(bool custom)`
- `public void SetDimensionIndex(int index)`
- `public virtual void SetDisabled(bool disabled)`
- `public virtual void SetFocus(bool focus)`
- `public virtual void SetGesture(bool gesture)`
- `public virtual void SetGestureMax(bool gesture)`
- `public virtual void SetGrab(bool grab)`
- `public virtual void SetInteractive(bool interactive)`
- `public virtual void SetObservation(bool observation)`
- `public virtual void SetObservationTargeted(bool targeted)`
- `public virtual void SetPhysicalTouch(bool touch)`
- `public virtual void SetPress(bool press)`
- `public virtual void SetTargeted(bool targeted)`
- `public virtual void SetToggled(bool toggled)`
- `public virtual void SetVisited(bool visited)`
- `public virtual void SetVoiceCommand(bool voice)`

<span data-ttu-id="ebfa9-336">**неаринтерактионтаучаблесурфаце**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-336">**NearInteractionTouchableSurface**</span></span>

<span data-ttu-id="ebfa9-337">`NearInteractionTouchableSurface`Класс был добавлен и теперь служит базовым классом для `NearInteractionTouchable` и `NearInteractionTouchableUnityUI` .</span><span class="sxs-lookup"><span data-stu-id="ebfa9-337">The `NearInteractionTouchableSurface` class has been added and now serves as the base class for `NearInteractionTouchable` and `NearInteractionTouchableUnityUI`.</span></span>

### <a name="profile-changes-in-210"></a><span data-ttu-id="ebfa9-338">Изменения профиля в 2.1.0</span><span class="sxs-lookup"><span data-stu-id="ebfa9-338">Profile changes in 2.1.0</span></span>

<span data-ttu-id="ebfa9-339">**Профиль отслеживания вручную**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-339">**Hand tracking profile**</span></span>

<span data-ttu-id="ebfa9-340">В сетке "рука" и в совместных визуализациях теперь есть отдельный редактор и параметры проигрывателя.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-340">The hand mesh and joint visualizations now have a separate editor and player settings.</span></span> <span data-ttu-id="ebfa9-341">Профиль отслеживания вручную был обновлен, чтобы разрешить установку этих визуализаций; Ничего, все, редактор или проигрыватель.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-341">The hand tracking profile has been updated to allow for setting these visualizations to; Nothing, Everything, Editor or Player.</span></span>

![Режимы визуализации вручную](../release-notes/images/HandTrackingVisualizationModes.png)

<span data-ttu-id="ebfa9-343">Для правильной работы с версией 2.1.0 может потребоваться обновить профили отслеживания пользовательских операций.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-343">Custom hand tracking profiles may need to be updated to work correctly with version 2.1.0.</span></span>

>[!NOTE]
><span data-ttu-id="ebfa9-344">Это изменение не обратно совместимо с версией 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-344">This change is not backwards compatible with version 2.0.0.</span></span>

<span data-ttu-id="ebfa9-345">**Профиль имитации ввода**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-345">**Input simulation profile**</span></span>

<span data-ttu-id="ebfa9-346">Система имитации ввода обновлена, что изменяет несколько параметров в профиле моделирования ввода.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-346">The input simulation system has been upgraded, which changes a few settings in the input simulation profile.</span></span> <span data-ttu-id="ebfa9-347">Некоторые изменения не могут быть перенесены автоматически, и пользователи могут обнаружить, что профили используют значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-347">Some changes can not be migrated automatically and users may find that profiles are using default values.</span></span>

1. <span data-ttu-id="ebfa9-348">Все привязки KeyCode и кнопок мыши в профиле заменены универсальной `KeyBinding` структурой, в которой хранится тип привязки (ключ или мышь), а также фактический код привязки (keyCode или номер кнопки мыши соответственно).</span><span class="sxs-lookup"><span data-stu-id="ebfa9-348">All KeyCode and mouse button bindings in the profile have been replaced with a generic `KeyBinding` struct, which stores the type of binding (key or mouse) as well as the actual binding code (KeyCode or mouse button number respectively).</span></span> <span data-ttu-id="ebfa9-349">Структура имеет собственный инспектор, который позволяет использовать единое отображение и предлагает средство "Автопривязка" для быстрого задания сочетаний клавиш, что позволяет быстро установить привязки к ключам, не выбирая из огромного раскрывающегося списка.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-349">The struct has its own inspector, which allows unified display and offers an "auto-bind" tool to quickly set key bindings by pressing the respective key instead of selecting from a huge dropdown list.</span></span>

    - <span data-ttu-id="ebfa9-350">фастконтролкэй</span><span class="sxs-lookup"><span data-stu-id="ebfa9-350">FastControlKey</span></span>
    - <span data-ttu-id="ebfa9-351">тогглелефсандкэй</span><span class="sxs-lookup"><span data-stu-id="ebfa9-351">ToggleLeftHandKey</span></span>
    - <span data-ttu-id="ebfa9-352">тогглеригхсандкэй</span><span class="sxs-lookup"><span data-stu-id="ebfa9-352">ToggleRightHandKey</span></span>
    - <span data-ttu-id="ebfa9-353">лефсандманипулатионкэй</span><span class="sxs-lookup"><span data-stu-id="ebfa9-353">LeftHandManipulationKey</span></span>
    - <span data-ttu-id="ebfa9-354">ригхсандманипулатионкэй</span><span class="sxs-lookup"><span data-stu-id="ebfa9-354">RightHandManipulationKey</span></span>

1. <span data-ttu-id="ebfa9-355">`MouseLookToggle` ранее был включен в `MouseLookButton` перечисление как `InputSimulationMouseButton.Focused` , теперь он является отдельным параметром.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-355">`MouseLookToggle` was previously included in the `MouseLookButton` enum as `InputSimulationMouseButton.Focused`, it is now a separate option.</span></span> <span data-ttu-id="ebfa9-356">Если этот параметр включен, Камера будет удерживать нажатой кнопку мыши после освобождения кнопки, пока не будет нажата клавиша Escape.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-356">When enabled, the camera will keep rotating with the mouse after releasing the button, until the escape key is pressed.</span></span>
1. <span data-ttu-id="ebfa9-357">`HandDepthMultiplier` значение по умолчанию было сокращено с 0,1 до 0,03, чтобы учесть некоторые изменения в моделировании ввода.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-357">`HandDepthMultiplier` default value has been lowered from 0.1 to 0.03 to accommodate some changes to the input simulation.</span></span> <span data-ttu-id="ebfa9-358">Если при прокрутке камера перемещается слишком быстро, попробуйте уменьшить это значение.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-358">If the camera moves too fast when scrolling, try lowering this value.</span></span>
1. <span data-ttu-id="ebfa9-359">Клавиши для поворота руки были удалены; поворот руки теперь также управляется мышью.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-359">Keys for rotating hands have been removed, hand rotation is now controlled by the mouse as well.</span></span> <span data-ttu-id="ebfa9-360">Удержание `HandRotateButton` (Ctrl) с помощью левого или правого ключа манипуляции (лшифт/Space) позволит включить поворот вручную.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-360">Holding `HandRotateButton` (Ctrl) together with the left/right hand manipulation key (LShift/Space) will enable hand rotation.</span></span>
1. <span data-ttu-id="ebfa9-361">В список входных осей появилась новая ось "вверх".</span><span class="sxs-lookup"><span data-stu-id="ebfa9-361">A new axis "UpDown" has been introduced to the input axis list.</span></span> <span data-ttu-id="ebfa9-362">Это управляет движением камеры в вертикальном и по умолчанию клавишами Q/E, а также кнопками триггера контроллера.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-362">This controls camera movement in the vertical and defaults to Q/E keys as well as the controller trigger buttons.</span></span>

<span data-ttu-id="ebfa9-363">Дополнительные сведения об этих изменениях см. в статье о [службе моделирования ввода](../features/input-simulation/input-simulation-service.md) .</span><span class="sxs-lookup"><span data-stu-id="ebfa9-363">For more information on these changes, please see the [input simulation service](../features/input-simulation/input-simulation-service.md) article.</span></span>

<span data-ttu-id="ebfa9-364">**Профиль поставщика данных мыши**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-364">**Mouse data provider profile**</span></span>

<span data-ttu-id="ebfa9-365">Профиль поставщика данных мыши был обновлен для предоставления новых `CursorSpeed` `WheelSpeed` свойств и.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-365">The mouse data provider profile has been updated to expose the new `CursorSpeed` and `WheelSpeed` properties.</span></span> <span data-ttu-id="ebfa9-366">Существующие настраиваемые профили будут автоматически иметь значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-366">Existing custom profiles will automatically have default values provided.</span></span> <span data-ttu-id="ebfa9-367">При сохранении профиля эти новые значения будут сохранены.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-367">When the profile is saved, these new values will be persisted.</span></span>

<span data-ttu-id="ebfa9-368">**Профиль сопоставления контроллеров**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-368">**Controller mapping profile**</span></span>

<span data-ttu-id="ebfa9-369">Некоторые оси и типы входных данных были обновлены в 2.1.0, особенно вокруг платформы Опенвр.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-369">Some axes and input types have been updated in 2.1.0, especially around the OpenVR platform.</span></span> <span data-ttu-id="ebfa9-370">При обновлении необходимо выбрать **микседреалититулкит-> Utilities-> профили сопоставления контроллеров >** .</span><span class="sxs-lookup"><span data-stu-id="ebfa9-370">Please be sure to select **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** when upgrading.</span></span> <span data-ttu-id="ebfa9-371">При этом будут обновлены все пользовательские профили сопоставления контроллеров с обновленными осями и данными, при этом пользовательские действия, назначенные пользователем, останутся без изменений.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-371">This will update any custom Controller Mapping Profiles with the updated axes and data, while leaving your custom-assigned input actions intact.</span></span>

## <a name="updating-rc2-to-200"></a><span data-ttu-id="ebfa9-372">Обновление RC2 до 2.0.0</span><span class="sxs-lookup"><span data-stu-id="ebfa9-372">Updating RC2 to 2.0.0</span></span>

<span data-ttu-id="ebfa9-373">между выпусками RC2 и 2.0.0 набор средств Microsoft Mixed Reality были внесены изменения, которые могут повлиять на существующие проекты.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-373">Between the RC2 and 2.0.0 releases of the Microsoft Mixed Reality Toolkit, changes were made that may impact existing projects.</span></span> <span data-ttu-id="ebfa9-374">В этом документе описаны эти изменения и способы обновления проектов до выпуска 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-374">This document describes those changes and how to update projects to the 2.0.0 release.</span></span>

- <span data-ttu-id="ebfa9-375">[изменения API](#api-changes-in-200);</span><span class="sxs-lookup"><span data-stu-id="ebfa9-375">[API changes](#api-changes-in-200)</span></span>
- [<span data-ttu-id="ebfa9-376">Изменения имени сборки</span><span class="sxs-lookup"><span data-stu-id="ebfa9-376">Assembly name changes</span></span>](#assembly-name-changes-in-200)

### <a name="api-changes-in-200"></a><span data-ttu-id="ebfa9-377">Изменения API в 2.0.0</span><span class="sxs-lookup"><span data-stu-id="ebfa9-377">API changes in 2.0.0</span></span>

<span data-ttu-id="ebfa9-378">С момента выпуска RC2 было внесено несколько изменений API, включая некоторые, которые могут нарушить работу существующих проектов.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-378">Since the release of RC2, there have been a number of API changes including some that may break existing projects.</span></span> <span data-ttu-id="ebfa9-379">В следующих разделах описаны изменения, произошедшие между выпусками RC2 и 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-379">The following sections describe the changes that have occurred between the RC2 and 2.0.0 releases.</span></span>

<span data-ttu-id="ebfa9-380">**MixedRealityToolkit;**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-380">**MixedRealityToolkit**</span></span>

<span data-ttu-id="ebfa9-381">Следующие общие свойства объекта Микседреалититулкит являются устаревшими.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-381">The following public properties on the MixedRealityToolkit object have been deprecated.</span></span>

- <span data-ttu-id="ebfa9-382">`RegisteredMixedRealityServices` больше не содержит коллекцию зарегистрированных расширений служб и поставщиков данных.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-382">`RegisteredMixedRealityServices` no longer contains the collection of registered extensions services and data providers.</span></span>

<span data-ttu-id="ebfa9-383">Для доступа к службам расширений используйте `MixedRealityServiceRegistry.TryGetService<T>` .</span><span class="sxs-lookup"><span data-stu-id="ebfa9-383">To access extension services, use `MixedRealityServiceRegistry.TryGetService<T>`.</span></span> <span data-ttu-id="ebfa9-384">Для доступа к поставщикам данных приведите экземпляр службы к [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) и используйте `GetDataProvider<T>` .</span><span class="sxs-lookup"><span data-stu-id="ebfa9-384">To access data providers, cast the service instance to [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) and use `GetDataProvider<T>`.</span></span>

<span data-ttu-id="ebfa9-385">Используйте [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) или [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) вместо этого для следующих устаревших свойств</span><span class="sxs-lookup"><span data-stu-id="ebfa9-385">Use [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) or [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) instead for the following deprecated properties</span></span>

- `ActiveSystems`
- `InputSystem`
- `BoundarySystem`
- `CameraSystem`
- `SpatialAwarenessSystem`
- `TeleportSystem`
- `DiagnosticsSystem`
- `SceneSystem`

<span data-ttu-id="ebfa9-386">**коресервицес**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-386">**CoreServices**</span></span>

<span data-ttu-id="ebfa9-387">[`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices)Класс является заменой для методов доступа статических систем (например: баундарисистем), найденных в `MixedRealityToolkit` объекте.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-387">The [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) class is the replacement for the static system accessors (ex: BoundarySystem) found in the `MixedRealityToolkit` object.</span></span>

>[!IMPORTANT]
><span data-ttu-id="ebfa9-388">`MixedRealityToolkit`Методы доступа к системе устарели в версии 2.0.0 и будут удалены в следующем выпуске мртк.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-388">The `MixedRealityToolkit` system accessors have been deprecated in version 2.0.0 and will be removed in a future release of the MRTK.</span></span>

<span data-ttu-id="ebfa9-389">В следующем примере кода показан старый и новый шаблон.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-389">The following code example illustrates the old and the new pattern.</span></span>

``` c#
// Old
GameObject playAreaVisualization = MixedRealityToolkit.BoundarySystem?.GetPlayAreaVisualization();

// New
GameObject playAreaVisualization = CoreServices.BoundarySystem?.GetPlayAreaVisualization();
```

<span data-ttu-id="ebfa9-390">Использование нового класса Коресистем гарантирует, что код приложения не будет обновляться, если вы измените приложение так, чтобы оно использовало другой регистратор служб (например, один из экспериментальных диспетчеров служб).</span><span class="sxs-lookup"><span data-stu-id="ebfa9-390">Using the new CoreSystem class will ensure that your application code will not need updating if you change the application to use a different service registrar (ex: one of the experimental service managers).</span></span>

<span data-ttu-id="ebfa9-391">**имикседреалитирайкастпровидер**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-391">**IMixedRealityRaycastProvider**</span></span>

<span data-ttu-id="ebfa9-392">После добавления Имикседреалитирайкастпровидер был изменен профиль конфигурации входной системы.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-392">With the addition of the IMixedRealityRaycastProvider, the input system configuration profile was changed.</span></span> <span data-ttu-id="ebfa9-393">Если у вас есть пользовательский профиль, при запуске приложения могут возникнуть ошибки на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-393">If you have a custom profile, you may receive the errors in the following image when you run your application.</span></span>

![Выбор поставщика Райкаст 1](../release-notes/images/UnableToRegisterRaycastProvider.png)

<span data-ttu-id="ebfa9-395">Чтобы исправить эти ошибки, добавьте экземпляр Имикседреалитирайкастпровидер в входной системный профиль.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-395">To fix these, please add an IMixedRealityRaycastProvider instance to your input system profile.</span></span>

![Выбор поставщика Райкаст 2](../release-notes/images/SelectRaycastProvider.png)

<span data-ttu-id="ebfa9-397">**Система событий**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-397">**Event System**</span></span>

- <span data-ttu-id="ebfa9-398">`IMixedRealityEventSystem`Старые методы API `Register` и `Unregister` были помечены как устаревшие.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-398">The `IMixedRealityEventSystem` old API methods `Register` and `Unregister` have been marked as obsolete.</span></span> <span data-ttu-id="ebfa9-399">Они сохраняются для обеспечения обратной совместимости.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-399">They are preserved for backwards compatibility.</span></span>
- <span data-ttu-id="ebfa9-400">`InputSystemGlobalListener` помечен как устаревший.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-400">`InputSystemGlobalListener` has been marked as obsolete.</span></span> <span data-ttu-id="ebfa9-401">Его функциональность не изменилась.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-401">Its functionality has not changed.</span></span>
- <span data-ttu-id="ebfa9-402">`BaseInputHandler` базовый класс был изменен с `InputSystemGlobalListener` на `InputSystemGlobalHandlerListener` .</span><span class="sxs-lookup"><span data-stu-id="ebfa9-402">`BaseInputHandler` base class has been changed from `InputSystemGlobalListener` to `InputSystemGlobalHandlerListener`.</span></span> <span data-ttu-id="ebfa9-403">Это критическое изменение для всех потомков `BaseInputHandler` .</span><span class="sxs-lookup"><span data-stu-id="ebfa9-403">This is a breaking change for any descendants of `BaseInputHandler`.</span></span>

<span data-ttu-id="ebfa9-404">**_Мотивация за изменение_**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-404">**_Motivation behind the change_**</span></span>

<span data-ttu-id="ebfa9-405">Старый API системы событий `Register` и `Unregister` потенциально может вызвать несколько проблем в среде выполнения:</span><span class="sxs-lookup"><span data-stu-id="ebfa9-405">The old event system API `Register` and `Unregister` could potentially cause multiple issues in runtime, main being:</span></span>

- <span data-ttu-id="ebfa9-406">Если компонент регистрируется для глобальных событий, он получит глобальные входные события *всех* типов.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-406">If a component registers for global events, it would receive global input events of *all* types.</span></span>
- <span data-ttu-id="ebfa9-407">Если один из компонентов объекта регистрируется для получения глобальных входных событий, все компоненты этого объекта будут иметь глобальные входные события *всех* типов.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-407">If one of the components on an object registers for global input events, all components on this object will receive global input events of *all* types.</span></span>
- <span data-ttu-id="ebfa9-408">Если два компонента одного и того же объекта регистрируются в глобальных событиях, а затем один из них отключен во время выполнения, второй останавливает получение глобальных событий.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-408">If two components on the same object register to global events, and then one is disabled in runtime, the second one stops receiving global events.</span></span>

<span data-ttu-id="ebfa9-409">Новый API `RegisterHandler` и `UnregisterHandler` :</span><span class="sxs-lookup"><span data-stu-id="ebfa9-409">New API `RegisterHandler` and `UnregisterHandler`:</span></span>

- <span data-ttu-id="ebfa9-410">Предоставляет явный и детализированный контроль над тем, какие входные события следует прослушивать глобально, а какие — на основе фокуса.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-410">Provides an explicit and granular control over which input events should be listened to globally and which should be focused-based.</span></span>
- <span data-ttu-id="ebfa9-411">Позволяет нескольким компонентам одного и того же объекта прослушивать глобальные события независимо друг от друга.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-411">Allows multiple components on the same object to listen to global events independently on each other.</span></span>

<span data-ttu-id="ebfa9-412">**_Как выполнить миграцию_**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-412">**_How to migrate_**</span></span>

- <span data-ttu-id="ebfa9-413">Если ранее вы вызывали `Register` / `Unregister` API непосредственно, замените эти вызовы вызовами метода `RegisterHandler` / `UnregisterHandler` .</span><span class="sxs-lookup"><span data-stu-id="ebfa9-413">If you have been calling `Register`/`Unregister` API directly before, replace these calls with calls to `RegisterHandler`/`UnregisterHandler`.</span></span> <span data-ttu-id="ebfa9-414">Используйте интерфейсы обработчика, которые реализуются как универсальные параметры.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-414">Use handler interfaces you implement as generic parameters.</span></span> <span data-ttu-id="ebfa9-415">Если вы реализуете несколько интерфейсов и несколько из них прослушивают глобальные события ввода, вызывайте их `RegisterHandler` несколько раз.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-415">If you implement multiple interfaces, and several of them listen to global input events, call `RegisterHandler` multiple times.</span></span>
- <span data-ttu-id="ebfa9-416">Если вы наследуете от `InputSystemGlobalListener` , измените наследование на `InputSystemGlobalHandlerListener` .</span><span class="sxs-lookup"><span data-stu-id="ebfa9-416">If you have been inheriting from `InputSystemGlobalListener`, change inheritance to `InputSystemGlobalHandlerListener`.</span></span> <span data-ttu-id="ebfa9-417">Реализуйте `RegisterHandlers` и `UnregisterHandlers` абстрактные методы.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-417">Implement `RegisterHandlers` and `UnregisterHandlers` abstract methods.</span></span> <span data-ttu-id="ebfa9-418">В вызове реализации `inputSystem.RegisterHandler` ( `inputSystem.UnregisterHandler` ) для регистрации всех интерфейсов обработчика, для которых требуется прослушивать глобальные события.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-418">In the implementation call `inputSystem.RegisterHandler` (`inputSystem.UnregisterHandler`) to register on all handler interfaces you want to listen global events for.</span></span>
- <span data-ttu-id="ebfa9-419">Если вы наследуете от `BaseInputHandler` , реализуйте `RegisterHandlers` и `UnregisterHandlers` абстрактные методы (то же, что и `InputSystemGlobalListener` ).</span><span class="sxs-lookup"><span data-stu-id="ebfa9-419">If you have been inheriting from `BaseInputHandler`, implement `RegisterHandlers` and `UnregisterHandlers` abstract methods (same as for `InputSystemGlobalListener`).</span></span>

<span data-ttu-id="ebfa9-420">**_Примеры миграции_**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-420">**_Examples of migration_**</span></span>

```c#
// Old
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.Register(gameObject);
    }

    private void OnDisable()
    {
        InputSystem?.Unregister(gameObject);
    }
}

// Migrated
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }
}
```

```c#
// Old
class SampleHandler2 : InputSystemGlobalListener, IMixedRealitySpeechHandler
{
}

// Migrated
class SampleHandler2 : InputSystemGlobalHandlerListener, IMixedRealitySpeechHandler
{
    private void RegisterHandlers()
    {
        InputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
    }

    private void UnregisterHandlers()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
    }
}

// Alternative migration
class SampleHandler2 : MonoBehaviour, IMixedRealitySpeechHandler
{
    private void OnEnable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }

    private void OnDisable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }
}
```

<span data-ttu-id="ebfa9-421">**Поддержка пространственных сведений**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-421">**Spatial Awareness**</span></span>

<span data-ttu-id="ebfa9-422">Интерфейсы Имикседреалитиспатиалаваренесссистем и Имикседреалитиспатиалаваренессобсервер использовали несколько критических изменений, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-422">The IMixedRealitySpatialAwarenessSystem and IMixedRealitySpatialAwarenessObserver interfaces have taken multiple breaking changes as described below.</span></span>

<span data-ttu-id="ebfa9-423">**_Изменения_**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-423">**_Changes_**</span></span>

<span data-ttu-id="ebfa9-424">Следующие методы были переименованы для лучшего описания их использования.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-424">The following method(s) have been renamed to better describe their usage.</span></span>

- <span data-ttu-id="ebfa9-425">`IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` был переименован в для `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` уточнения его использования.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-425">`IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` has been renamed to `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` to clarify its usage.</span></span>

<span data-ttu-id="ebfa9-426">**_Добавления_**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-426">**_Additions_**</span></span>

<span data-ttu-id="ebfa9-427">На основе отзывов клиентов была добавлена поддержка простого удаления ранее просмотренных данных о пространственной осведомленности.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-427">Based on customer feedback, support for easy removal of previously observed spatial awareness data has been added.</span></span>

- `IMixedRealitySpatialAwarenessSystem.ClearObservations()`
- `IMixedRealitySpatialAwarenessSystem.ClearObservations<T>(string name)`
- `IMixedRealitySpatialAwarenessObserver.ClearObservations()`

<span data-ttu-id="ebfa9-428">**Решатели**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-428">**Solvers**</span></span>

<span data-ttu-id="ebfa9-429">Некоторые компоненты поиска решения и класс Солверхандлер Manager были изменены для устранения различных ошибок и для более интуитивного использования.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-429">Some solver components and the SolverHandler manager class has changed to fix various bugs and for more intuitive usage.</span></span>

<span data-ttu-id="ebfa9-430">**_солверхандлер_**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-430">**_SolverHandler_**</span></span>

- <span data-ttu-id="ebfa9-431">Класс больше не расширяется с `ControllerFinder`</span><span class="sxs-lookup"><span data-stu-id="ebfa9-431">Class no longer extends from `ControllerFinder`</span></span>
- <span data-ttu-id="ebfa9-432">`TrackedObjectToReference` общедоступное свойство устарело и было переименовано в `TrackedTargetType`</span><span class="sxs-lookup"><span data-stu-id="ebfa9-432">`TrackedObjectToReference` public property deprecated and has been renamed to `TrackedTargetType`</span></span>
- <span data-ttu-id="ebfa9-433">`TrackedObjectType` устаревшие левые & правильные значения контроллера.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-433">`TrackedObjectType` deprecates left & right controller values.</span></span> <span data-ttu-id="ebfa9-434">Вместо этого `MotionController` Используйте `HandJoint` значения или и обновите новое `TrackedHandedness` свойство, чтобы ограничить отслеживание до левого или правого контроллера.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-434">Instead use `MotionController` or `HandJoint` values and update new `TrackedHandedness` property to limit tracking to left or right controller</span></span>

<span data-ttu-id="ebfa9-435">**_Промежуточное_**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-435">**_InBetween_**</span></span>

- <span data-ttu-id="ebfa9-436">`TrackedObjectForSecondTransform` общедоступное свойство устарело и было переименовано в `SecondTrackedObjectType`</span><span class="sxs-lookup"><span data-stu-id="ebfa9-436">`TrackedObjectForSecondTransform` public property deprecated and has been renamed to `SecondTrackedObjectType`</span></span>
- <span data-ttu-id="ebfa9-437">`AttachSecondTransformToNewTrackedObject()` был удален.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-437">`AttachSecondTransformToNewTrackedObject()` has been removed.</span></span> <span data-ttu-id="ebfa9-438">Чтобы обновить Поиск решения, измените открытые свойства (т. е.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-438">To update the solver, modify the public properties (i.e</span></span> <span data-ttu-id="ebfa9-439">`SecondTrackedObjectType`)</span><span class="sxs-lookup"><span data-stu-id="ebfa9-439">`SecondTrackedObjectType`)</span></span>

<span data-ttu-id="ebfa9-440">**_сурфацемагнетисм_**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-440">**_SurfaceMagnetism_**</span></span>

- <span data-ttu-id="ebfa9-441">`MaxDistance` общедоступное свойство устарело и было переименовано в `MaxRaycastDistance`</span><span class="sxs-lookup"><span data-stu-id="ebfa9-441">`MaxDistance` public property deprecated and has been renamed to `MaxRaycastDistance`</span></span>
- <span data-ttu-id="ebfa9-442">`CloseDistance` общедоступное свойство устарело и было переименовано в `ClosestDistance`</span><span class="sxs-lookup"><span data-stu-id="ebfa9-442">`CloseDistance` public property deprecated and has been renamed to `ClosestDistance`</span></span>
- <span data-ttu-id="ebfa9-443">Значение по умолчанию для параметра `RaycastDirectionMode` , `TrackedTargetForward` которое теперь райкастс в направлении перенаправленного целевого преобразования</span><span class="sxs-lookup"><span data-stu-id="ebfa9-443">Default value for `RaycastDirectionMode` is now `TrackedTargetForward` which raycasts in the direction of the tracked target transform forward</span></span>
- <span data-ttu-id="ebfa9-444">`OrientationMode` значения Enum `Vertical` и `Full` переименованы в `TrackedTarget` и `SurfaceNormal` соответственно</span><span class="sxs-lookup"><span data-stu-id="ebfa9-444">`OrientationMode` enum values, `Vertical` and `Full`, have been renamed to `TrackedTarget` and `SurfaceNormal` respectively</span></span>
- <span data-ttu-id="ebfa9-445">`KeepOrientationVertical` Добавлено открытое свойство, определяющее, остается ли ориентация связанных GameObject по вертикали</span><span class="sxs-lookup"><span data-stu-id="ebfa9-445">`KeepOrientationVertical` public property has been added to control whether orientation of associated GameObject remains vertical</span></span>

<span data-ttu-id="ebfa9-446">**Кнопки**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-446">**Buttons**</span></span>

- <span data-ttu-id="ebfa9-447">[`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) Теперь `DistanceSpaceMode` свойство имеет значение `Local` по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-447">[`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) now has `DistanceSpaceMode` property set to `Local` as default.</span></span> <span data-ttu-id="ebfa9-448">Это позволяет масштабировать кнопки, пока они продолжают нажимать</span><span class="sxs-lookup"><span data-stu-id="ebfa9-448">This allows buttons to be scaled while still be pressable</span></span>

<span data-ttu-id="ebfa9-449">**Обрезка сферы**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-449">**Clipping Sphere**</span></span>

<span data-ttu-id="ebfa9-450">Интерфейс Клиппингсфере изменился на зеркальное отображение интерфейсов API, находящихся в Клиппингбокс и Клиппингплане.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-450">The ClippingSphere interface has changed to mirror the APIs found in the ClippingBox and ClippingPlane.</span></span>

<span data-ttu-id="ebfa9-451">Свойство RADIUS Клиппингсфере теперь неявно вычисляется на основе шкалы преобразования.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-451">The ClippingSphere's Radius property is now implicitly calculated based on the transform scale.</span></span> <span data-ttu-id="ebfa9-452">Прежде чем разработчики должны будут указать радиус Клиппингсфере в инспекторе.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-452">Before developers would have to specify the radius of the ClippingSphere in the inspector.</span></span> <span data-ttu-id="ebfa9-453">Если вы хотите изменить радиус, просто обновите масштаб преобразования преобразования, как обычно.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-453">If you want to change the radius, just update the transform scale of the transform as you normally would.</span></span>

<span data-ttu-id="ebfa9-454">**Неаринтерактионтаучабле и Покепоинтер**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-454">**NearInteractionTouchable and PokePointer**</span></span>

- <span data-ttu-id="ebfa9-455">Неаринтерактионтаучабле не обрабатывает доступ к холсту пользовательского интерфейса Unity больше.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-455">NearInteractionTouchable does not handle Unity UI canvas touching any longer.</span></span> <span data-ttu-id="ebfa9-456">Теперь класс Неаринтерактионтаучаблеунитюи должен использоваться для таучаблес пользовательского интерфейса Unity.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-456">The NearInteractionTouchableUnityUI class must be used for Unity UI touchables now.</span></span>
- <span data-ttu-id="ebfa9-457">Коллидернеаринтерактионтаучабле — это новый базовый класс для таучаблес, основанный на конфликтах, т. е. Каждый сенсорный ввод, кроме Неаринтерактионтаучаблеунитюи.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-457">ColliderNearInteractionTouchable is the new base class for touchables based on colliders, i.e. every touchable except NearInteractionTouchableUnityUI.</span></span>
- <span data-ttu-id="ebfa9-458">Басенеаринтерактионтаучабле. Дистфронт был перемещен и переименован в Покепоинтер. Таучабледистанце это расстояние, которое Покепоинтер может взаимодействовать с touchables.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-458">BaseNearInteractionTouchable.DistFront has been moved and renamed to PokePointer.TouchableDistance This is the distance and which the PokePointer can interact with touchables.</span></span> <span data-ttu-id="ebfa9-459">Раньше каждый сенсорный ввод имеет свое максимальное расстояние взаимодействия, но теперь он определен в Покепоинтер, что позволяет оптимизировать оптимизацию.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-459">Previously each touchable had its own maximum interaction distance, but now this is defined in the PokePointer which allows better optimization.</span></span>
- <span data-ttu-id="ebfa9-460">Басенеаринтерактионтаучабле. Дистбакк был переименован в Покесрешолд. Это позволяет ясно, что Покесрешолд является аналогом Дебаунцесрешолд.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-460">BaseNearInteractionTouchable.DistBack has been renamed to PokeThreshold This makes it clear that PokeThreshold is the counterpart to DebounceThreshold.</span></span> <span data-ttu-id="ebfa9-461">Сенсорный элемент активируется, когда Покесрешолд пересекается и освобождается при пересечении Дебаунцесрешолд.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-461">A touchable is activated when the PokeThreshold is crossed, and released when DebounceThreshold is crossed.</span></span>

<span data-ttu-id="ebfa9-462">**ReadOnlyAttribute**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-462">**ReadOnlyAttribute**</span></span>

<span data-ttu-id="ebfa9-463">`Microsoft.MixedReality.Toolkit`Пространство имен было добавлено в `ReadOnlyAttribute` , `BeginReadOnlyGroupAttribute` и `EndReadOnlyGroupAttribute` .</span><span class="sxs-lookup"><span data-stu-id="ebfa9-463">The `Microsoft.MixedReality.Toolkit` namespace has been added to `ReadOnlyAttribute`, `BeginReadOnlyGroupAttribute`, and `EndReadOnlyGroupAttribute`.</span></span>

<span data-ttu-id="ebfa9-464">**поинтеркликкхандлер**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-464">**PointerClickHandler**</span></span>

<span data-ttu-id="ebfa9-465">Класс `PointerClickHandler` не рекомендуется к использованию.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-465">The `PointerClickHandler` class has been deprecated.</span></span> <span data-ttu-id="ebfa9-466">`PointerHandler`Вместо этого следует использовать функцию, которая предоставляет те же функциональные возможности.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-466">The `PointerHandler` should be used instead, it provides the same functionality.</span></span>

<span data-ttu-id="ebfa9-467">**поддержка HoloLens нажатием кнопки**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-467">**HoloLens clicker support**</span></span>

<span data-ttu-id="ebfa9-468">сопоставления контроллера HoloLensного щелчка не изменяются, [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) чтобы быть необработанными [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand) .</span><span class="sxs-lookup"><span data-stu-id="ebfa9-468">The HoloLens clicker's controller mappings have changed from being an unhanded [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) to being an unhanded [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand).</span></span> <span data-ttu-id="ebfa9-469">Для этой учетной записи автоматическое обновление будет выполняться при первом открытии профиля Контроллермаппинг.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-469">To account for this, an automatic updater will run the first time you open your ControllerMapping profile.</span></span> <span data-ttu-id="ebfa9-470">Чтобы активировать этот одноразовый шаг миграции, откройте какие-либо пользовательские профили по крайней мере один раз после обновления до 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-470">Please open any custom profiles at least once after upgrading to 2.0.0 in order to trigger this one-time migration step.</span></span>

<span data-ttu-id="ebfa9-471">**интерактаблехигхлигхт**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-471">**InteractableHighlight**</span></span>

<span data-ttu-id="ebfa9-472">Класс `InteractableHighlight` не рекомендуется к использованию.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-472">The `InteractableHighlight` class has been deprecated.</span></span> <span data-ttu-id="ebfa9-473">`InteractableOnFocus` `FocusInteractableStates` Вместо этого следует использовать класс и ресурс.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-473">The `InteractableOnFocus` class and `FocusInteractableStates` asset should be used instead.</span></span> <span data-ttu-id="ebfa9-474">чтобы создать новый `Theme` ресурс для, щелкните `InteractableOnFocus` правой кнопкой мыши в окне проекта и выберите пункт *создать*  >  *смешанную реальность набор средств*  >  *взаимодействующей*  >  *теме*.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-474">To create a new `Theme` asset for the `InteractableOnFocus`, right click in the project window and select *Create* > *Mixed Reality Toolkit* > *Interactable* > *Theme*.</span></span>

<span data-ttu-id="ebfa9-475">**хандинтерактионпанзум**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-475">**HandInteractionPanZoom**</span></span>

<span data-ttu-id="ebfa9-476">`HandInteractionPanZoom` был перемещен в пространство имен пользовательского интерфейса, так как он не был входным компонентом.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-476">`HandInteractionPanZoom` has been moved to the UI namespace as it was not an input component.</span></span> <span data-ttu-id="ebfa9-477">`HandPanEventData` также было перемещено в это пространство имен и упрощено для соответствия с другими данными событий пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-477">`HandPanEventData` has also been moved into this namespace, and simplified to correspond with other UI event data.</span></span>

### <a name="assembly-name-changes-in-200"></a><span data-ttu-id="ebfa9-478">Изменение имени сборки в 2.0.0</span><span class="sxs-lookup"><span data-stu-id="ebfa9-478">Assembly name changes in 2.0.0</span></span>

<span data-ttu-id="ebfa9-479">в выпуске 2.0.0 все официальные имена сборок смешанной набор средств реальности и связанные с ними файлы определения сборки (. асмдеф) были обновлены в соответствии со следующим шаблоном.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-479">In The 2.0.0 release, all of the official Mixed Reality Toolkit assembly names and their associated assembly definition (.asmdef) files have been updated to fit the following pattern.</span></span>

```c#
Microsoft.MixedReality.Toolkit[.<name>]
```

<span data-ttu-id="ebfa9-480">В некоторых случаях объединено несколько сборок для создания лучшего Unity их содержимого.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-480">In some instances, multiple assemblies have been merged to create better unity of their contents.</span></span> <span data-ttu-id="ebfa9-481">Если в проекте используются пользовательские файлы. асмдеф, они могут потребовать обновления.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-481">If your project uses custom .asmdef files, they may require updating.</span></span>

<span data-ttu-id="ebfa9-482">В следующих таблицах описывается, как имена файлов RC2. асмдеф сопоставлены с выпуском 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-482">The following tables describe how the RC2 .asmdef file names map to the 2.0.0 release.</span></span> <span data-ttu-id="ebfa9-483">Все имена сборок соответствуют имени файла асмдеф.</span><span class="sxs-lookup"><span data-stu-id="ebfa9-483">All assembly names match the .asmdef file name.</span></span>

<span data-ttu-id="ebfa9-484">**MixedRealityToolkit;**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-484">**MixedRealityToolkit**</span></span>

| <span data-ttu-id="ebfa9-485">RC2</span><span class="sxs-lookup"><span data-stu-id="ebfa9-485">RC2</span></span> | <span data-ttu-id="ebfa9-486">2.0.0</span><span class="sxs-lookup"><span data-stu-id="ebfa9-486">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="ebfa9-487">Микседреалититулкит. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-487">MixedRealityToolkit.asmdef</span></span> | <span data-ttu-id="ebfa9-488">Microsoft. Микседреалити. набор средств. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-488">Microsoft.MixedReality.Toolkit.asmdef</span></span> |
| <span data-ttu-id="ebfa9-489">Микседреалититулкит. Core. Буилданддеплой. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-489">MixedRealityToolkit.Core.BuildAndDeploy.asmdef</span></span> | <span data-ttu-id="ebfa9-490">Microsoft. Микседреалити. набор средств. Редактор. Буилданддеплой. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-490">Microsoft.MixedReality.Toolkit.Editor.BuildAndDeploy.asmdef</span></span> |
| <span data-ttu-id="ebfa9-491">Микседреалититулкит. Core. definitions. Utilities. Editor. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-491">MixedRealityToolkit.Core.Definitions.Utilities.Editor.asmdef</span></span> | <span data-ttu-id="ebfa9-492">Удалено, используйте Microsoft. Микседреалити. набор средств. Редактор. Utilities. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-492">Removed, use Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span></span> |
| <span data-ttu-id="ebfa9-493">Микседреалититулкит. Core. Extensions. Едиторклассекстенсионс. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-493">MixedRealityToolkit.Core.Extensions.EditorClassExtensions.asmdef</span></span> | <span data-ttu-id="ebfa9-494">Microsoft. Микседреалити. набор средств. Редактор. Классекстенсионс. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-494">Microsoft.MixedReality.Toolkit.Editor.ClassExtensions.asmdef</span></span>
| <span data-ttu-id="ebfa9-495">Микседреалититулкит. Core. Инспекторы. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-495">MixedRealityToolkit.Core.Inspectors.asmdef</span></span> | <span data-ttu-id="ebfa9-496">Microsoft. Микседреалити. набор средств. Редактор. Инспекторы. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-496">Microsoft.MixedReality.Toolkit.Editor.Inspectors.asmdef</span></span> |
| <span data-ttu-id="ebfa9-497">Микседреалититулкит. Core. Инспекторы. Сервицеинспекторс. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-497">MixedRealityToolkit.Core.Inspectors.ServiceInspectors.asmdef</span></span> | <span data-ttu-id="ebfa9-498">Microsoft. Микседреалити. набор средств. Редактор. Сервицеинспекторс. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-498">Microsoft.MixedReality.Toolkit.Editor.ServiceInspectors.asmdef</span></span> |
| <span data-ttu-id="ebfa9-499">Микседреалититулкит. Core. Утилитиесасинк. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-499">MixedRealityToolkit.Core.UtilitiesAsync.asmdef</span></span> | <span data-ttu-id="ebfa9-500">Microsoft. Микседреалити. набор средств. Async. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-500">Microsoft.MixedReality.Toolkit.Async.asmdef</span></span> |
| <span data-ttu-id="ebfa9-501">Микседреалититулкит. Core. Utilities. Editor. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-501">MixedRealityToolkit.Core.Utilities.Editor.asmdef</span></span> | <span data-ttu-id="ebfa9-502">Microsoft. Микседреалити. набор средств. Редактор. Utilities. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-502">Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span></span> |
| <span data-ttu-id="ebfa9-503">Микседреалититулкит. Utilities. Глтф. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-503">MixedRealityToolkit.Utilities.Gltf.asmdef</span></span> | <span data-ttu-id="ebfa9-504">Microsoft. Микседреалити. набор средств. Глтф. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-504">Microsoft.MixedReality.Toolkit.Gltf.asmdef</span></span> |
| <span data-ttu-id="ebfa9-505">Микседреалититулкит. Utilities. Глтф. импортеров. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-505">MixedRealityToolkit.Utilities.Gltf.Importers.asmdef</span></span> | <span data-ttu-id="ebfa9-506">Microsoft. Микседреалити. набор средств. Глтф. импортеров. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-506">Microsoft.MixedReality.Toolkit.Gltf.Importers.asmdef</span></span> |

<span data-ttu-id="ebfa9-507">**Микседреалититулкит. Providers**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-507">**MixedRealityToolkit.Providers**</span></span>

| <span data-ttu-id="ebfa9-508">RC2</span><span class="sxs-lookup"><span data-stu-id="ebfa9-508">RC2</span></span> | <span data-ttu-id="ebfa9-509">2.0.0</span><span class="sxs-lookup"><span data-stu-id="ebfa9-509">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="ebfa9-510">Микседреалититулкит. Providers. Опенвр. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-510">MixedRealityToolkit.Providers.OpenVR.asmdef</span></span> | <span data-ttu-id="ebfa9-511">Microsoft. Микседреалити. набор средств. Providers. Опенвр. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-511">Microsoft.MixedReality.Toolkit.Providers.OpenVR.asmdef</span></span> |
| <span data-ttu-id="ebfa9-512">Микседреалититулкит. Providers. Виндовсмикседреалити. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-512">MixedRealityToolkit.Providers.WindowsMixedReality.asmdef</span></span> | <span data-ttu-id="ebfa9-513">Microsoft. Микседреалити. набор средств. Providers. Виндовсмикседреалити. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-513">Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.asmdef</span></span> |
| <span data-ttu-id="ebfa9-514">Микседреалититулкит. Providers. Виндовсвоицеинпут. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-514">MixedRealityToolkit.Providers.WindowsVoiceInput.asmdef</span></span> | <span data-ttu-id="ebfa9-515">Microsoft. Микседреалити. набор средств. Providers. Виндовсвоицеинпут. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-515">Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput.asmdef</span></span> |

<span data-ttu-id="ebfa9-516">**Микседреалититулкит. Services**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-516">**MixedRealityToolkit.Services**</span></span>

| <span data-ttu-id="ebfa9-517">RC2</span><span class="sxs-lookup"><span data-stu-id="ebfa9-517">RC2</span></span> | <span data-ttu-id="ebfa9-518">2.0.0</span><span class="sxs-lookup"><span data-stu-id="ebfa9-518">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="ebfa9-519">Микседреалититулкит. Services. Баундарисистем. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-519">MixedRealityToolkit.Services.BoundarySystem.asmdef</span></span> | <span data-ttu-id="ebfa9-520">Microsoft. Микседреалити. набор средств. Services. Баундарисистем. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-520">Microsoft.MixedReality.Toolkit.Services.BoundarySystem.asmdef</span></span> |
| <span data-ttu-id="ebfa9-521">Микседреалититулкит. Services. Камерасистем. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-521">MixedRealityToolkit.Services.CameraSystem.asmdef</span></span> | <span data-ttu-id="ebfa9-522">Microsoft. Микседреалити. набор средств. Services. Камерасистем. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-522">Microsoft.MixedReality.Toolkit.Services.CameraSystem.asmdef</span></span> |
| <span data-ttu-id="ebfa9-523">Микседреалититулкит. Services. Диагностикссистем. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-523">MixedRealityToolkit.Services.DiagnosticsSystem.asmdef</span></span> | <span data-ttu-id="ebfa9-524">Microsoft. Микседреалити. набор средств. Services. Диагностикссистем. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-524">Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem.asmdef</span></span> |
| <span data-ttu-id="ebfa9-525">Микседреалититулкит. Services. Инпутсимулатион. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-525">MixedRealityToolkit.Services.InputSimulation.asmdef</span></span> | <span data-ttu-id="ebfa9-526">Microsoft. Микседреалити. набор средств. Services. Инпутсимулатион. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-526">Microsoft.MixedReality.Toolkit.Services.InputSimulation.asmdef</span></span> |
| <span data-ttu-id="ebfa9-527">Микседреалититулкит. Services. Инпутсимулатион. Editor. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-527">MixedRealityToolkit.Services.InputSimulation.Editor.asmdef</span></span> | <span data-ttu-id="ebfa9-528">Microsoft. Микседреалити. набор средств. Services. Инпутсимулатион. Editor. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-528">Microsoft.MixedReality.Toolkit.Services.InputSimulation.Editor.asmdef</span></span> |
| <span data-ttu-id="ebfa9-529">Микседреалититулкит. Services. Инпутсистем. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-529">MixedRealityToolkit.Services.InputSystem.asmdef</span></span> | <span data-ttu-id="ebfa9-530">Microsoft. Микседреалити. набор средств. Services. Инпутсистем. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-530">Microsoft.MixedReality.Toolkit.Services.InputSystem.asmdef</span></span> |
| <span data-ttu-id="ebfa9-531">Микседреалититулкит. Services. Инспекторы. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-531">MixedRealityToolkit.Services.Inspectors.asmdef</span></span> | <span data-ttu-id="ebfa9-532">Microsoft. Микседреалити. набор средств. Services. Инпутсистем. Editor. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-532">Microsoft.MixedReality.Toolkit.Services.InputSystem.Editor.asmdef</span></span> |
| <span data-ttu-id="ebfa9-533">Микседреалититулкит. Services. Сценесистем. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-533">MixedRealityToolkit.Services.SceneSystem.asmdef</span></span> | <span data-ttu-id="ebfa9-534">Microsoft. Микседреалити. набор средств. Services. Сценесистем. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-534">Microsoft.MixedReality.Toolkit.Services.SceneSystem.asmdef</span></span> |
| <span data-ttu-id="ebfa9-535">Микседреалититулкит. Services. Спатиалаваренесссистем. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-535">MixedRealityToolkit.Services.SpatialAwarenessSystem.asmdef</span></span> | <span data-ttu-id="ebfa9-536">Microsoft. Микседреалити. набор средств. Services. Спатиалаваренесссистем. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-536">Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem.asmdef</span></span> |
| <span data-ttu-id="ebfa9-537">Микседреалититулкит. Services. Телепортсистем. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-537">MixedRealityToolkit.Services.TeleportSystem.asmdef</span></span> | <span data-ttu-id="ebfa9-538">Microsoft. Микседреалити. набор средств. Services. Телепортсистем. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-538">Microsoft.MixedReality.Toolkit.Services.TeleportSystem.asmdef</span></span> |

<span data-ttu-id="ebfa9-539">**Микседреалититулкит. SDK**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-539">**MixedRealityToolkit.SDK**</span></span>

| <span data-ttu-id="ebfa9-540">RC2</span><span class="sxs-lookup"><span data-stu-id="ebfa9-540">RC2</span></span> | <span data-ttu-id="ebfa9-541">2.0.0</span><span class="sxs-lookup"><span data-stu-id="ebfa9-541">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="ebfa9-542">Микседреалититулкит. SDK. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-542">MixedRealityToolkit.SDK.asmdef</span></span> | <span data-ttu-id="ebfa9-543">Microsoft. Микседреалити. набор средств. Пакет SDK. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-543">Microsoft.MixedReality.Toolkit.SDK.asmdef</span></span> |
| <span data-ttu-id="ebfa9-544">Микседреалититулкит. SDK. Инспекторы. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-544">MixedRealityToolkit.SDK.Inspectors.asmdef</span></span> | <span data-ttu-id="ebfa9-545">Microsoft. Микседреалити. набор средств. Tool. Инспекторы. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-545">Microsoft.MixedReality.Toolkit.SDK.Inspectors.asmdef</span></span> |

<span data-ttu-id="ebfa9-546">**Микседреалититулкит. примеры**</span><span class="sxs-lookup"><span data-stu-id="ebfa9-546">**MixedRealityToolkit.Examples**</span></span>

| <span data-ttu-id="ebfa9-547">RC2</span><span class="sxs-lookup"><span data-stu-id="ebfa9-547">RC2</span></span> | <span data-ttu-id="ebfa9-548">2.0.0</span><span class="sxs-lookup"><span data-stu-id="ebfa9-548">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="ebfa9-549">Микседреалититулкит. examples. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-549">MixedRealityToolkit.Examples.asmdef</span></span> | <span data-ttu-id="ebfa9-550">Microsoft. Микседреалити. набор средств. Примеры. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-550">Microsoft.MixedReality.Toolkit.Examples.asmdef</span></span> |
| <span data-ttu-id="ebfa9-551">Микседреалититулкит. examples. Демонстрация. Глтф. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-551">MixedRealityToolkit.Examples.Demos.Gltf.asmdef</span></span> | <span data-ttu-id="ebfa9-552">Microsoft. Микседреалити. набор средств. Демонстрация. Глтф. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-552">Microsoft.MixedReality.Toolkit.Demos.Gltf.asmdef</span></span> |
| <span data-ttu-id="ebfa9-553">Микседреалититулкит. examples. демонстрации. Стандардшадер. Инспекторы. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-553">MixedRealityToolkit.Examples.Demos.StandardShader.Inspectors.asmdef</span></span> | <span data-ttu-id="ebfa9-554">Microsoft. Микседреалити. набор средств. Демонстрационные версии. Стандардшадер. Инспекторы. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-554">Microsoft.MixedReality.Toolkit.Demos.StandardShader.Inspectors.asmdef</span></span> |
| <span data-ttu-id="ebfa9-555">Микседреалититулкит. examples. Демонстрация. Utilities. Инспекторфиелдс. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-555">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.asmdef</span></span> | <span data-ttu-id="ebfa9-556">Microsoft. Микседреалити. набор средств. Демонстрация. Инспекторфиелдс. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-556">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.asmdef</span></span> |
| <span data-ttu-id="ebfa9-557">Микседреалититулкит. examples. демонстрации. Utilities. Инспекторфиелдс. Инспекторы. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-557">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.Inspectors.asmdef</span></span> | <span data-ttu-id="ebfa9-558">Microsoft. Микседреалити. набор средств. Демонстрационные версии. Инспекторфиелдс. Инспекторы. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-558">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.Inspectors.asmdef</span></span> |
| <span data-ttu-id="ebfa9-559">Микседреалититулкит. examples. Демонстрация. UX. Интерактаблес. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-559">MixedRealityToolkit.Examples.Demos.UX.Interactables.asmdef</span></span> | <span data-ttu-id="ebfa9-560">Microsoft. Микседреалити. набор средств. Демонстрация. UX. Интерактаблес. асмдеф</span><span class="sxs-lookup"><span data-stu-id="ebfa9-560">Microsoft.MixedReality.Toolkit.Demos.UX.Interactables.asmdef</span></span> |
