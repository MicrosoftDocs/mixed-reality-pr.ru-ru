---
title: Разработка собственных иммерсивных сред
description: В дополнение к домашним средам Windows Mixed Reality мы предоставляем, вы можете поэкспериментировать с созданием и использованием собственных.
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality, Смешанная реальность, виртуальная реальность, VR, MR, Главная, пользовательские среды, места, Клифф House, скилофт, пользователь, создать
ms.openlocfilehash: 69fac9fcc0b3d7f199f4277c5d1b5a0c7df5f8c2
ms.sourcegitcommit: 838bebf6bacac4047feff493c0847d4e6371976f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2020
ms.locfileid: "91781522"
---
# <a name="design-your-own-immersive-environments"></a><span data-ttu-id="a3da5-104">Разработка собственных иммерсивных сред</span><span class="sxs-lookup"><span data-stu-id="a3da5-104">Design your own immersive environments</span></span>

>[!NOTE]
><span data-ttu-id="a3da5-105">Это экспериментальная функция.</span><span class="sxs-lookup"><span data-stu-id="a3da5-105">This is an experimental feature.</span></span> <span data-ttu-id="a3da5-106">Попробуйте и протестируйте его, но не удивитсь, если все работает не так, как ожидалось.</span><span class="sxs-lookup"><span data-stu-id="a3da5-106">Give it a try and have fun with it, but don't be surprised if everything doesn't quite work as expected.</span></span> <span data-ttu-id="a3da5-107">Мы оцениваем жизнеспособность этой функции и предлагаем вам ее использовать, поэтому Расскажите нам о своем опыте (и всех обнаруженных ошибках) на [форумах разработчиков](https://forums.hololens.com/categories/custom-home-environments).</span><span class="sxs-lookup"><span data-stu-id="a3da5-107">We're evaluating the viability of this feature and interest in using it, so please tell us about your experience (and any bugs you've found) in the [developer forums](https://forums.hololens.com/categories/custom-home-environments).</span></span>

<span data-ttu-id="a3da5-108">Начиная с [обновления Windows 10 от апреля 2018](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)г. Мы включили экспериментальную функцию, позволяющую добавлять пользовательские среды в средство выбора мест (в меню Пуск) для использования в качестве [домашней страницы Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md).</span><span class="sxs-lookup"><span data-stu-id="a3da5-108">Starting with the [Windows 10 April 2018 update](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018), we've enabled an experimental feature that lets you add custom environments to the Places picker (on the Start menu) to use as the [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md).</span></span> <span data-ttu-id="a3da5-109">В Windows Mixed Reality есть две среды по умолчанию — Клифф House и Скилофт, которые можно выбрать в качестве домашней.</span><span class="sxs-lookup"><span data-stu-id="a3da5-109">Windows Mixed Reality has two default environments, Cliff House and Skyloft, that you can choose as your home.</span></span> <span data-ttu-id="a3da5-110">Создание пользовательских сред позволяет развернуть этот список с помощью собственных операций создания.</span><span class="sxs-lookup"><span data-stu-id="a3da5-110">Creating custom environments allows you to expand that list with your own creations.</span></span> <span data-ttu-id="a3da5-111">Мы предоставляем эту возможность в раннем состоянии, чтобы оценить интерес от создателей и разработчиков, узнать, какие типы миров вы создаете, и понять, как работать с различными средствами разработки.</span><span class="sxs-lookup"><span data-stu-id="a3da5-111">We are making this available in an early state to evaluate interest from creators and developers, see what kinds of worlds you create, and understand how you work with different authoring tools.</span></span>

<span data-ttu-id="a3da5-112">При использовании пользовательской среды вы заметите, что телеперенос, взаимодействие с приложениями и размещение голограмм работает так же, как и в Клифф House и Скилофт.</span><span class="sxs-lookup"><span data-stu-id="a3da5-112">When using a custom environment you'll notice that teleporting, interacting with apps, and placing holograms works just like it does in the Cliff House and Skyloft.</span></span> <span data-ttu-id="a3da5-113">Вы можете просматривать веб-сайт в фэнтези альбоме или заполнять футуристическихй город с голограммами. возможности бесконечно!</span><span class="sxs-lookup"><span data-stu-id="a3da5-113">You can browse the web in a fantasy landscape or fill a futuristic city with holograms - the possibilities are endless!</span></span>

## <a name="device-support"></a><span data-ttu-id="a3da5-114">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="a3da5-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a3da5-115"><strong>Возможность</strong></span><span class="sxs-lookup"><span data-stu-id="a3da5-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="a3da5-116"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="a3da5-116"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="a3da5-117"><a href="../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="a3da5-117"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a3da5-118">Пользовательские домашние среды</span><span class="sxs-lookup"><span data-stu-id="a3da5-118">Custom home environments</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="a3da5-119">✔️</span><span class="sxs-lookup"><span data-stu-id="a3da5-119">✔️</span></span></td>
    </tr>
</table>

## <a name="trying-a-sample-environment"></a><span data-ttu-id="a3da5-120">Попытка использования примера среды</span><span class="sxs-lookup"><span data-stu-id="a3da5-120">Trying a sample environment</span></span>

<span data-ttu-id="a3da5-121">Мы создали пример среды, который показывает некоторые творческие возможности пользовательских домашних сред.</span><span class="sxs-lookup"><span data-stu-id="a3da5-121">We've created a sample environment that shows off some of the creative possibilities of custom home environments.</span></span> <span data-ttu-id="a3da5-122">Выполните следующие действия, чтобы испытать это:</span><span class="sxs-lookup"><span data-stu-id="a3da5-122">Follow these steps to try it out:</span></span>
1. <span data-ttu-id="a3da5-123">[Скачайте наш пример фэнтези среды](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (ссылки на самораспаковывающийся исполняемый файл).</span><span class="sxs-lookup"><span data-stu-id="a3da5-123">[Download our sample Fantasy Island environment](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (link points to self-extracting executable).</span></span>

    <span data-ttu-id="a3da5-124">![Пример среды фэнтези](images/FantasyLand.jpg)</span><span class="sxs-lookup"><span data-stu-id="a3da5-124">![Fantasy Island sample environment](images/FantasyLand.jpg)</span></span><br>
    <span data-ttu-id="a3da5-125">*Пример среды фэнтези*</span><span class="sxs-lookup"><span data-stu-id="a3da5-125">*Fantasy Island sample environment*</span></span><br>

2. <span data-ttu-id="a3da5-126">Запустите только что скачанный файл **Fantasy_Island.exe** .</span><span class="sxs-lookup"><span data-stu-id="a3da5-126">Run the **Fantasy_Island.exe** file you just downloaded.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a3da5-127">При попытке запустить exe-файл, скачанный из Интернета (например, этот), может появиться всплывающее окно «защищенный компьютер Windows».</span><span class="sxs-lookup"><span data-stu-id="a3da5-127">When attempting to run a .exe file downloaded from the web (like this one), you may encounter a "Windows protected your PC" pop-up.</span></span> <span data-ttu-id="a3da5-128">Чтобы запустить Fantasy_Island.exe из этого всплывающего окна, выберите **Дополнительные сведения** , а затем **выполните все равно** .</span><span class="sxs-lookup"><span data-stu-id="a3da5-128">To run Fantasy_Island.exe from this pop-up, select **More info** and then **Run anyway** .</span></span> <span data-ttu-id="a3da5-129">Этот параметр безопасности предназначен для защиты от загрузки файлов, которые не следует доверять, поэтому выбирайте этот параметр только в том случае, если вы доверяете источнику файла.</span><span class="sxs-lookup"><span data-stu-id="a3da5-129">This security setting is meant to protect you from downloading files you may not want to trust, so please only choose this option when you trust the source of the file.</span></span>

3. <span data-ttu-id="a3da5-130">Откройте **проводник** и перейдите к папке Environments, вставляя следующую строку в адресной строке: `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState` .</span><span class="sxs-lookup"><span data-stu-id="a3da5-130">Open **File Explorer** and navigate to the environments folder by pasting the following in the address bar: `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`.</span></span>
4. <span data-ttu-id="a3da5-131">Скопируйте образец окружения, скачанный в эту папку.</span><span class="sxs-lookup"><span data-stu-id="a3da5-131">Copy the sample environment that you downloaded into this folder.</span></span>
5. <span data-ttu-id="a3da5-132">Перезапустите **портал смешанной реальности** .</span><span class="sxs-lookup"><span data-stu-id="a3da5-132">Restart **Mixed Reality Portal** .</span></span> <span data-ttu-id="a3da5-133">Это приведет к обновлению списка сред в средстве выбора мест.</span><span class="sxs-lookup"><span data-stu-id="a3da5-133">This will refresh the list of environments in the Places picker.</span></span>
6. <span data-ttu-id="a3da5-134">Установите на гарнитуру.</span><span class="sxs-lookup"><span data-stu-id="a3da5-134">Put on your headset.</span></span> <span data-ttu-id="a3da5-135">Когда Вы находитесь на домашней странице, откройте **меню Пуск** с помощью кнопки Windows вашего контроллера.</span><span class="sxs-lookup"><span data-stu-id="a3da5-135">Once you're in the home, open the **Start menu** using the Windows button your controller.</span></span>
7. <span data-ttu-id="a3da5-136">Щелкните значок **мест** над списком закрепленных приложений, чтобы выбрать домашнюю среду.</span><span class="sxs-lookup"><span data-stu-id="a3da5-136">Select the **Places** icon above the list of pinned apps to choose a home environment.</span></span>
8. <span data-ttu-id="a3da5-137">Вы найдете среду острова фэнтези, скачанную в списке мест.</span><span class="sxs-lookup"><span data-stu-id="a3da5-137">You will find the Fantasy Island environment that you downloaded in your list of places.</span></span> <span data-ttu-id="a3da5-138">Выберите **остров фэнтези** , чтобы ввести новую пользовательскую домашнюю среду!</span><span class="sxs-lookup"><span data-stu-id="a3da5-138">Select **Fantasy Island** to enter your new custom home environment!</span></span>

## <a name="creating-your-own-custom-environment"></a><span data-ttu-id="a3da5-139">Создание собственной настраиваемой среды</span><span class="sxs-lookup"><span data-stu-id="a3da5-139">Creating your own custom environment</span></span>

<span data-ttu-id="a3da5-140">Помимо использования наших примеров сред вы можете экспортировать собственные среды, используя любимое программное обеспечение трехмерного редактирования.</span><span class="sxs-lookup"><span data-stu-id="a3da5-140">In addition to using our sample environments, you can export your own custom environments using your favorite 3D editing software.</span></span> 

### <a name="modeling-guidelines"></a><span data-ttu-id="a3da5-141">Рекомендации по моделированию</span><span class="sxs-lookup"><span data-stu-id="a3da5-141">Modeling guidelines</span></span>

<span data-ttu-id="a3da5-142">При моделировании среды учитывайте следующие рекомендации.</span><span class="sxs-lookup"><span data-stu-id="a3da5-142">When modeling your environment, keep the following recommendations in mind.</span></span> <span data-ttu-id="a3da5-143">Это поможет обеспечить правильную ориентацию пользователя в белиеваблим мире:</span><span class="sxs-lookup"><span data-stu-id="a3da5-143">This will help ensure the user spawns in the correct orientation in a believably-sized world:</span></span>

1. <span data-ttu-id="a3da5-144">Пользователи будут порождаться в 0, 0, 0, чтобы по центру, куда вы хотите поначаль, посередине происхождения.</span><span class="sxs-lookup"><span data-stu-id="a3da5-144">Users will spawn at 0,0,0 so center your desired spawn location around the origin.</span></span>
2. <span data-ttu-id="a3da5-145">Для рабочих единиц должно быть задано значение измерительные единицы, чтобы ресурсы можно было создавать в масштабе мира.</span><span class="sxs-lookup"><span data-stu-id="a3da5-145">Working Units should be set to meters so that assets can be authored at world scale.</span></span>
3. <span data-ttu-id="a3da5-146">Для оси up должно быть задано значение "Y".</span><span class="sxs-lookup"><span data-stu-id="a3da5-146">The Up axis should be set to “Y”.</span></span>
4. <span data-ttu-id="a3da5-147">Ресурс должен иметь значение "Forward", направленное на положительную ось Z.</span><span class="sxs-lookup"><span data-stu-id="a3da5-147">The asset should face “forward” towards the positive Z axis.</span></span>
5. <span data-ttu-id="a3da5-148">Все сетки не нужно объединять, но рекомендуется при использовании устройств с ограниченными ресурсами.</span><span class="sxs-lookup"><span data-stu-id="a3da5-148">All meshes do not need to be combined, but it is recommended if you are targeting resource-constrained devices.</span></span>

### <a name="exporting-your-environment"></a><span data-ttu-id="a3da5-149">Экспорт среды</span><span class="sxs-lookup"><span data-stu-id="a3da5-149">Exporting your environment</span></span>

<span data-ttu-id="a3da5-150">Windows Mixed Reality использует двоичный Глтф (. GLBA) в качестве формата доставки ресурсов для сред.</span><span class="sxs-lookup"><span data-stu-id="a3da5-150">Windows Mixed Reality relies on binary glTF (.glb) as the asset delivery format for environments.</span></span> <span data-ttu-id="a3da5-151">Глтф — это прямой бесплатный открытый стандарт для доставки трехмерных ресурсов, поддерживаемый группой Кхронос.</span><span class="sxs-lookup"><span data-stu-id="a3da5-151">glTF is a royalty free open standard for 3D asset delivery maintained by the Khronos group.</span></span> <span data-ttu-id="a3da5-152">Так как Глтф развивается как промышленный стандарт для взаимодействия с трехмерным содержимым, корпорация Майкрософт будет поддерживать формат для приложений и интерфейсов Windows.</span><span class="sxs-lookup"><span data-stu-id="a3da5-152">As glTF evolves as an industry standard for interoperable 3D content, so will Microsoft’s support for the format across Windows apps and experiences.</span></span>

<span data-ttu-id="a3da5-153">Первый шаг в экспорте ресурсов для использования в качестве пользовательских домашних сред — создание модели Глтф 2,0.</span><span class="sxs-lookup"><span data-stu-id="a3da5-153">The first step in exporting assets to be used as custom home environments is generating a glTF 2.0 model.</span></span> <span data-ttu-id="a3da5-154">Рабочая группа Глтф содержит [список поддерживаемых экспортов и конвертеров](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) для создания модели глтф 2,0.</span><span class="sxs-lookup"><span data-stu-id="a3da5-154">The glTF working group maintains a [list of supported exporters and converters](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) to create a glTF 2.0 model.</span></span> <span data-ttu-id="a3da5-155">Чтобы приступить к работе, используйте одну из программ, перечисленных на этой странице, для создания и экспорта модели Глтф 2,0 или преобразования существующей модели с помощью одного из поддерживаемых преобразователей.</span><span class="sxs-lookup"><span data-stu-id="a3da5-155">To get started, use one of the programs listed on this page to create and export a glTF 2.0 model, or convert an existing model using one of the supported converters.</span></span>

<span data-ttu-id="a3da5-156">Кроме того, ознакомьтесь с [этой полезной статьей](https://www.khronos.org/blog/art-pipeline-for-gltf) , в которой приводится обзор рабочего процесса для экспорта моделей Глтф из Blend и 3ds Max напрямую.</span><span class="sxs-lookup"><span data-stu-id="a3da5-156">Additionally, check out [this helpful article](https://www.khronos.org/blog/art-pipeline-for-gltf) which provides an overview of an art workflow for exporting glTF models from Blender and 3DS Max directly.</span></span> 

### <a name="environment-limits"></a><span data-ttu-id="a3da5-157">Ограничения среды</span><span class="sxs-lookup"><span data-stu-id="a3da5-157">Environment limits</span></span>

<span data-ttu-id="a3da5-158">Все среды должны иметь < 256 МБ.</span><span class="sxs-lookup"><span data-stu-id="a3da5-158">All environments must be < 256 mbs.</span></span> <span data-ttu-id="a3da5-159">В средах, превышающих 256 MBS, не удастся загрузиться и будет возвращаться к пустому миру с помощью скибокс по умолчанию, окружающего пользователя.</span><span class="sxs-lookup"><span data-stu-id="a3da5-159">Environments larger than 256 mbs will fail to load and fall back to an empty world with just the default skybox surrounding the user.</span></span> <span data-ttu-id="a3da5-160">При создании моделей имейте в виду, что этот размер файла не имеет значения.</span><span class="sxs-lookup"><span data-stu-id="a3da5-160">Please keep this file size limit in mind when creating your models.</span></span> <span data-ttu-id="a3da5-161">Кроме того, если вы планируете оптимизировать среду с помощью Виндовсмрассетконвертер, как описано ниже, то компания cognizant, что размер текстуры увеличится, так как оптимизатор создает текстуры с большим размером файла, но быстрее загружается.</span><span class="sxs-lookup"><span data-stu-id="a3da5-161">Additionally, if you plan to optimize your environment using the WindowsMRAssetConverter as described below, be cognizant that the texture size will increase as the optimizer creates textures that have a larger file size, but load faster.</span></span> 

### <a name="optimizing-your-environment"></a><span data-ttu-id="a3da5-162">Оптимизация среды</span><span class="sxs-lookup"><span data-stu-id="a3da5-162">Optimizing your environment</span></span>

<span data-ttu-id="a3da5-163">Windows Mixed Reality поддерживает ряд дополнительных оптимизаций, которые значительно снижают время загрузки сред.</span><span class="sxs-lookup"><span data-stu-id="a3da5-163">Windows Mixed Reality supports a number of optional optimizations that will significantly reduce the load time of your environments.</span></span> <span data-ttu-id="a3da5-164">Это может быть особенно важно для сред со многими текстурами, так как иногда время ожидания истекает при загрузке.</span><span class="sxs-lookup"><span data-stu-id="a3da5-164">This can be especially important for environments with many textures, as they will sometimes time out while loading.</span></span> <span data-ttu-id="a3da5-165">Как правило, этот шаг рекомендуется для всех ресурсов, однако небольшие среды с небольшим или низким разрешением не всегда занимают этого.</span><span class="sxs-lookup"><span data-stu-id="a3da5-165">In general, we recommend this step for all assets, however, smaller environments with few or low-resolution textures won't always require it.</span></span> 

<span data-ttu-id="a3da5-166">Чтобы упростить этот процесс, мы создали [конвертер активов Windows Mixed Reality (доступный на сайте GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases) для оптимизации.</span><span class="sxs-lookup"><span data-stu-id="a3da5-166">To make this process easier, we have created the [Windows Mixed Reality Asset Converter (available on GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases) to perform your optimizations.</span></span> <span data-ttu-id="a3da5-167">Это средство использует набор служебных программ, доступных в Microsoft Глтф Toolkit, для оптимизации любых стандартных 2,0 Глтф или. GLBA, выполняя дополнительную упаковку, сжатие и разрешающее масштабирование текстуры.</span><span class="sxs-lookup"><span data-stu-id="a3da5-167">This tool uses a set of utilities available in the Microsoft glTF toolkit to optimize any standard 2.0 glTF or .glb by performing an additional texture packing, compression and resolution down-scaling.</span></span> 

<span data-ttu-id="a3da5-168">Сейчас преобразователь поддерживает ряд флагов, позволяющих настроить точное поведение оптимизации.</span><span class="sxs-lookup"><span data-stu-id="a3da5-168">The converter currently supports a number of flags to tweak the exact behavior of the optimizations.</span></span> <span data-ttu-id="a3da5-169">Для достижения лучших результатов рекомендуется использовать следующие флаги:</span><span class="sxs-lookup"><span data-stu-id="a3da5-169">We recommend running with the following flags for best results:</span></span>

<span data-ttu-id="a3da5-170">Флаг</span><span class="sxs-lookup"><span data-stu-id="a3da5-170">Flag</span></span>|<span data-ttu-id="a3da5-171">Рекомендуемые значения</span><span class="sxs-lookup"><span data-stu-id="a3da5-171">Recommended Value(s)</span></span>|<span data-ttu-id="a3da5-172">Описание</span><span class="sxs-lookup"><span data-stu-id="a3da5-172">Description</span></span>
---|---|---
<span data-ttu-id="a3da5-173">-Max-текстура-размер</span><span class="sxs-lookup"><span data-stu-id="a3da5-173">-max-texture-size</span></span>|<span data-ttu-id="a3da5-174">1024 или 2048</span><span class="sxs-lookup"><span data-stu-id="a3da5-174">1024 or 2048</span></span>| <span data-ttu-id="a3da5-175">Настройте его, чтобы улучшить качество текстур, по умолчанию — 512 x 512.</span><span class="sxs-lookup"><span data-stu-id="a3da5-175">Tweak this to improve the quality of the textures, default is 512x512.</span></span> <span data-ttu-id="a3da5-176">Обратите внимание, что большее значение значительно влияет на размер файла окружения, поэтому необходимо учитывать ограничение в 256 МБ.</span><span class="sxs-lookup"><span data-stu-id="a3da5-176">Note that a larger value will significantly impact the file size of the environment so keep the 256 mb limit in mind</span></span>
<span data-ttu-id="a3da5-177">-min-Version</span><span class="sxs-lookup"><span data-stu-id="a3da5-177">-min-version</span></span>|<span data-ttu-id="a3da5-178">1803</span><span class="sxs-lookup"><span data-stu-id="a3da5-178">1803</span></span>|<span data-ttu-id="a3da5-179">Пользовательские среды поддерживаются только в версиях Windows >= 1803.</span><span class="sxs-lookup"><span data-stu-id="a3da5-179">Custom environments are only supported on versions of windows >= 1803.</span></span> <span data-ttu-id="a3da5-180">Этот флаг приведет к удалению текстур для более старых версий и уменьшению размера файла окончательного ресурса</span><span class="sxs-lookup"><span data-stu-id="a3da5-180">This flag will remove textures for older versions and reduce the file size of the final asset</span></span>

<span data-ttu-id="a3da5-181">Пример:</span><span class="sxs-lookup"><span data-stu-id="a3da5-181">For example:</span></span>

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a><span data-ttu-id="a3da5-182">Тестирование среды</span><span class="sxs-lookup"><span data-stu-id="a3da5-182">Testing your environment</span></span>

<span data-ttu-id="a3da5-183">Создав окончательную среду. GLBA, вы готовы протестировать ее на гарнитуре.</span><span class="sxs-lookup"><span data-stu-id="a3da5-183">Once you have your final .glb environment you're ready to test it out in the headset.</span></span> <span data-ttu-id="a3da5-184">Начните с шага 2 в разделе ["попытка выборки среды"](#trying-a-sample-environment) , чтобы использовать пользовательскую среду в качестве домашней среды смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="a3da5-184">Start at step 2 in the ["Trying a sample environment"](#trying-a-sample-environment) section to use your custom environment as the mixed reality home.</span></span> 

## <a name="feedback"></a><span data-ttu-id="a3da5-185">Отзывы</span><span class="sxs-lookup"><span data-stu-id="a3da5-185">Feedback</span></span>

<span data-ttu-id="a3da5-186">Хотя мы оцениваем эту экспериментальную функцию, мы заинтересованы в изучении того, как вы используете пользовательские среды, какие ошибки могут возникнуть и как вам нравится эта функция.</span><span class="sxs-lookup"><span data-stu-id="a3da5-186">While we're evaluating this experimental feature, we're interested in learning how you're using custom environments, any bugs you may encounter, and how you like the feature.</span></span> <span data-ttu-id="a3da5-187">Поделитесь всеми отзывами о создании и использовании пользовательских домашних сред на [форумах разработчиков](https://forums.hololens.com/categories/custom-home-environments).</span><span class="sxs-lookup"><span data-stu-id="a3da5-187">Please share any and all feedback for creating and using custom home environments in the [developer forums](https://forums.hololens.com/categories/custom-home-environments).</span></span>

## <a name="troubleshooting-and-tips"></a><span data-ttu-id="a3da5-188">Устранение неполадок и советы</span><span class="sxs-lookup"><span data-stu-id="a3da5-188">Troubleshooting and tips</span></span>

### <a name="how-do-i-change-the-name-of-the-environment"></a><span data-ttu-id="a3da5-189">Разделы справки изменить имя окружения?</span><span class="sxs-lookup"><span data-stu-id="a3da5-189">How do I change the name of the environment?</span></span>

<span data-ttu-id="a3da5-190">Имя файла в папке среды будет использоваться в средстве выбора мест.</span><span class="sxs-lookup"><span data-stu-id="a3da5-190">The file name in the environments folder will be used in the Places picker.</span></span> <span data-ttu-id="a3da5-191">Чтобы изменить имя среды, просто переименуйте имя файла среды, а затем перезапустите портал смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="a3da5-191">To change the name of your environment simply rename the environment file name, and then restart Mixed Reality Portal.</span></span>

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a><span data-ttu-id="a3da5-192">Разделы справки удалить пользовательские среды из средства выбора "Мои расположения"?</span><span class="sxs-lookup"><span data-stu-id="a3da5-192">How do I remove custom environments from my Places picker?</span></span>

<span data-ttu-id="a3da5-193">Чтобы удалить пользовательскую среду, откройте папку среды на компьютере ( `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState` ) и удалите среду.</span><span class="sxs-lookup"><span data-stu-id="a3da5-193">To remove a custom environment, open the environments folder on your PC (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) and delete the environment.</span></span> <span data-ttu-id="a3da5-194">После перезапуска портала смешанной реальности эта среда больше не будет отображаться в средстве выбора мест.</span><span class="sxs-lookup"><span data-stu-id="a3da5-194">Once you restart Mixed Reality Portal, this environment will no longer appear in the Places picker.</span></span> 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a><span data-ttu-id="a3da5-195">Разделы справки по умолчанию в мою любимую пользовательскую среду?</span><span class="sxs-lookup"><span data-stu-id="a3da5-195">How do I default to my favorite custom environment?</span></span>

<span data-ttu-id="a3da5-196">В настоящее время вы не можете изменить среду по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a3da5-196">You can't currently change the default environment.</span></span> <span data-ttu-id="a3da5-197">Каждый раз, когда вы перезапустите портал смешанной реальности, вы вернетесь в среду Клифф House.</span><span class="sxs-lookup"><span data-stu-id="a3da5-197">Each time you restart Mixed Reality Portal, you will be returned to the Cliff House environment.</span></span> 

### <a name="i-spawn-into-a-blank-space"></a><span data-ttu-id="a3da5-198">Я попытался создать пустое пространство</span><span class="sxs-lookup"><span data-stu-id="a3da5-198">I spawn into a blank space</span></span>

<span data-ttu-id="a3da5-199">Windows Mixed Reality [не поддерживает среды, размер которых превышает 256 МБ](#environment-limits).</span><span class="sxs-lookup"><span data-stu-id="a3da5-199">Windows Mixed Reality [doesn't support environments that exceed 256 mb](#environment-limits).</span></span> <span data-ttu-id="a3da5-200">Если среда превышает это ограничение, вы попадете на пустое поле перевозки без модели.</span><span class="sxs-lookup"><span data-stu-id="a3da5-200">When an environment exceeds this limit, you will land in the empty sky box with no model.</span></span>

### <a name="it-takes-a-long-time-to-load-my-environment"></a><span data-ttu-id="a3da5-201">Загрузка моей среды занимает много времени</span><span class="sxs-lookup"><span data-stu-id="a3da5-201">It takes a long time to load my environment</span></span>

<span data-ttu-id="a3da5-202">В среду можно добавить дополнительные оптимизации, чтобы ускорить загрузку.</span><span class="sxs-lookup"><span data-stu-id="a3da5-202">You can add optional optimizations to your environment to make it load faster.</span></span> <span data-ttu-id="a3da5-203">Дополнительные сведения см. [в разделе "Оптимизация среды"](#optimizing-your-environment) .</span><span class="sxs-lookup"><span data-stu-id="a3da5-203">See ["Optimizing your environment"](#optimizing-your-environment) for details.</span></span>

### <a name="the-scale-of-my-environment-is-incorrect"></a><span data-ttu-id="a3da5-204">Неправильная шкала моей среды</span><span class="sxs-lookup"><span data-stu-id="a3da5-204">The scale of my environment is incorrect</span></span>

<span data-ttu-id="a3da5-205">Windows Mixed Reality преобразует единицы Глтф в один счетчик при загрузке сред.</span><span class="sxs-lookup"><span data-stu-id="a3da5-205">Windows Mixed Reality translates glTF units to 1 meter when loading environments.</span></span> <span data-ttu-id="a3da5-206">Если среда загружает непредвиденный масштаб, дважды проверьте свой экспорт, чтобы убедиться, что вы выполняете моделирование на одной шкале измерения.</span><span class="sxs-lookup"><span data-stu-id="a3da5-206">If your environment loads up an unexpected scale, double check your exporter to ensure that you're modeling at a 1 meter scale.</span></span> 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a><span data-ttu-id="a3da5-207">Неверное место порождения в моей среде</span><span class="sxs-lookup"><span data-stu-id="a3da5-207">The spawn location in my environment is incorrect</span></span>

<span data-ttu-id="a3da5-208">Расположение порождений по умолчанию находится в среде 0, 0, 0.</span><span class="sxs-lookup"><span data-stu-id="a3da5-208">The default spawn location is located at 0,0,0 in the environment.</span></span> <span data-ttu-id="a3da5-209">В настоящее время его невозможно настроить, поэтому необходимо изменить порожденную точку, экспортировав среду с исходным расположением в нужной точке порождения.</span><span class="sxs-lookup"><span data-stu-id="a3da5-209">Its not currently possible to customize this location, so you must modify the spawn point by exporting your environment with the origin positioned at the desired spawn point.</span></span>

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a><span data-ttu-id="a3da5-210">Звук не звучит правильно в окружении</span><span class="sxs-lookup"><span data-stu-id="a3da5-210">The audio doesn't sound correct in the environment</span></span>

<span data-ttu-id="a3da5-211">При создании пользовательской среды будет использоваться моделирование визуализации акустических характеристик, не совпадающее с созданным физическим пространством.</span><span class="sxs-lookup"><span data-stu-id="a3da5-211">When you create your custom environment, it will be using an acoustics rendering simulation that does not match the physical space you have created.</span></span> <span data-ttu-id="a3da5-212">Звук может поступать из неправильных направлений и может показаться муффледным.</span><span class="sxs-lookup"><span data-stu-id="a3da5-212">Sound may come from the wrong directions and may sound muffled.</span></span> 

## <a name="see-also"></a><span data-ttu-id="a3da5-213">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a3da5-213">See also</span></span>
* [<span data-ttu-id="a3da5-214">Конвертер активов Windows Mixed Reality (на GitHub)</span><span class="sxs-lookup"><span data-stu-id="a3da5-214">Windows Mixed Reality Asset Converter (on GitHub)</span></span>](https://github.com/Microsoft/glTF-Toolkit/releases)
