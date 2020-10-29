---
title: Пространственный звук в Unreal
description: Подробные сведения о подключаемом модуле пространственного звука для Unreal Engine.
author: hferrone
ms.author: v-hferrone
ms.date: 06/15/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, потоковая передача, удаленное взаимодействие, смешанная реальность, разработка, начало работы, функции, новый проект, эмулятор, документация, руководства, функции, голограммы, разработка игр
ms.openlocfilehash: 9b953cd0ea9aab92b2306da63a948b470363d0e6
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91702114"
---
# <a name="spatial-audio-in-unreal"></a><span data-ttu-id="3b8b5-104">Пространственный звук в Unreal</span><span class="sxs-lookup"><span data-stu-id="3b8b5-104">Spatial Audio in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="3b8b5-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="3b8b5-105">Overview</span></span>

<span data-ttu-id="3b8b5-106">В отличие от зрения, человеческий слух может воспринимать звуки в пространстве с охватом в 360 градусов.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-106">Unlike vision, humans hear in 360 degree surround sound.</span></span> <span data-ttu-id="3b8b5-107">Система пространственного звука эмулирует человеческий слух, предоставляя ориентиры для определения расположения источников звука в пространстве.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-107">Spatial sound emulates how human hearing works, providing the cues needed to identify sound locations in world-space.</span></span> <span data-ttu-id="3b8b5-108">Добавив систему пространственного звука в свои приложения смешанной реальности, вы сделаете их более иммерсивными для пользователей.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-108">When you add spatial sound in your mixed reality applications, you're enhancing the level of immersion your users experience.</span></span>  

<span data-ttu-id="3b8b5-109">Высококачественная обработка пространственного звука очень сложна, поэтому HoloLens 2 поставляется со специальным оборудованием для обработки звуковых объектов.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-109">High quality spatial sound processing is complex, so the HoloLens 2 comes with dedicated hardware for processing those sound objects.</span></span>  <span data-ttu-id="3b8b5-110">Прежде чем вы сможете воспользоваться этим оборудованием, вам нужно установить подключаемый модуль **MicrosoftSpatialSound** в своем проекте Unreal.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-110">Before you can access this hardware processing support, you'll need to install the **MicrosoftSpatialSound** plugin in your Unreal project.</span></span> <span data-ttu-id="3b8b5-111">С помощью этой статьи вы сможете установить и настроить этот подключаемый модуль и найти дополнительные ресурсы об использовании пространственного звука в Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-111">This article will walk you through the installation and configuration of that plugin and point you towards more in-depth resources for using spatial sound in the Unreal engine.</span></span>

## <a name="installing-the-microsoft-spatial-sound-plugin"></a><span data-ttu-id="3b8b5-112">Установка подключаемого модуля пространственного звука (Майкрософт)</span><span class="sxs-lookup"><span data-stu-id="3b8b5-112">Installing the Microsoft Spatial Sound plugin</span></span>

<span data-ttu-id="3b8b5-113">Первый шаг по добавлению системы пространственного звука в проект заключается в установке подключаемого модуля пространственного звука (Майкрософт), который можно найти следующим образом:</span><span class="sxs-lookup"><span data-stu-id="3b8b5-113">The first step to adding spatial sound to your project is installing the Microsoft Spatial Sound plugin, which you can find by:</span></span>

1. <span data-ttu-id="3b8b5-114">Щелкните **Edit > Plugins** (Правка > Подключаемые модули) и введите **MicrosoftSpatialSound** в поле поиска.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-114">Clicking **Edit > Plugins** and searching for **MicrosoftSpatialSound** in the search box.</span></span>
2. <span data-ttu-id="3b8b5-115">Установите флажок **Enabled** (Включен) для подключаемого модуля **MicrosoftSpatialSound** .</span><span class="sxs-lookup"><span data-stu-id="3b8b5-115">Selecting the **Enabled** checkbox in the **MicrosoftSpatialSound** plugin.</span></span>
3. <span data-ttu-id="3b8b5-116">Перезапустите Unreal Editor, выбрав **Restart Now** (Перезапустить) на странице подключаемого модуля.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-116">Restarting the Unreal Editor by selecting **Restart Now** from the plugins page.</span></span>

> [!NOTE]
> <span data-ttu-id="3b8b5-117">Если вы еще этого не сделали, установите подключаемые модули **Microsoft Windows Mixed Reality** и **HoloLens** , выполнив инструкции из раздела **[Инициализация проекта](tutorials/unreal-uxt-ch2.md)** нашей серии руководств по Unreal.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-117">If you haven't already, you'll need to install the **Microsoft Windows Mixed Reality** and **HoloLens** plugins by following the instructions in the **[Initializing your project](tutorials/unreal-uxt-ch2.md)** section of our Unreal tutorial series.</span></span>

![Подключаемый модуль пространственного звука для Unreal](images/unreal-spatial-audio-img-01.png)

<span data-ttu-id="3b8b5-119">После перезапуска редактора вы сможете работать с проектом.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-119">Once the editor restarts, your project is all set!</span></span>


## <a name="setting-the-spatialization-plugin-for-hololens-2-platform"></a><span data-ttu-id="3b8b5-120">Настройка подключаемого модуля пространственной обработки для платформы HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3b8b5-120">Setting the spatialization plugin for HoloLens 2 platform</span></span>
<span data-ttu-id="3b8b5-121">Настройка подключаемого модуля пространственной обработки осуществляется отдельно для каждой платформы.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-121">Configuring the spatialization plugin is done on a per-platform basis.</span></span>  <span data-ttu-id="3b8b5-122">Вы можете включить подключаемый модуль пространственного звука (Майкрософт) для HoloLens 2 следующим образом:</span><span class="sxs-lookup"><span data-stu-id="3b8b5-122">You can enable the Microsoft Spatial Sound plugin for the HoloLens 2 by:</span></span>
1. <span data-ttu-id="3b8b5-123">Выберите **Edit > Project Settings** (Правка > Параметры проекта), прокрутите до параметра **Platforms** (Платформы) и щелкните **HoloLens** .</span><span class="sxs-lookup"><span data-stu-id="3b8b5-123">Selecting **Edit > Project Settings** , scrolling to **Platforms** and clicking **HoloLens** .</span></span>
2. <span data-ttu-id="3b8b5-124">Разверните свойства **Audio** (Аудио) и укажите в поле **Spatialization Plugin** (Подключаемый модуль пространственной обработки) значение **Microsoft Spatial Sound** (Пространственный звук (Майкрософт)).</span><span class="sxs-lookup"><span data-stu-id="3b8b5-124">Expanding the **Audio** properties and setting the **Spatialization Plugin** field to **Microsoft Spatial Sound** .</span></span>

![Подключаемый модуль пространственной обработки для платформы HoloLens](images/unreal-spatial-audio-img-02.png)

<span data-ttu-id="3b8b5-126">Если вы планируете тестировать свое приложение в Unreal Editor на компьютере, вам понадобится повторить приведенные выше шаги для платформы **Windows** :</span><span class="sxs-lookup"><span data-stu-id="3b8b5-126">If you're going to be previewing your application in the Unreal editor on a desktop PC, you'll need to repeat the above steps for the **Windows** platform:</span></span>

![Подключаемый модуль пространственной обработки для платформы Windows](images/unreal-spatial-audio-img-05.png)

## <a name="enabling-spatial-audio-on-your-workstation"></a><span data-ttu-id="3b8b5-128">Включение пространственного звука на рабочей станции</span><span class="sxs-lookup"><span data-stu-id="3b8b5-128">Enabling spatial audio on your workstation</span></span>
<span data-ttu-id="3b8b5-129">Пространственный звук по умолчанию отключен для настольных версий Windows.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-129">Spatial audio is disabled by default on desktop versions of Windows.</span></span> <span data-ttu-id="3b8b5-130">Его можно включить следующим образом:</span><span class="sxs-lookup"><span data-stu-id="3b8b5-130">You can enable it by:</span></span>
* <span data-ttu-id="3b8b5-131">Щелкните правой кнопкой мыши значок **громкости** на панели задач.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-131">Right-clicking on the **volume** icon in the task bar.</span></span>
    + <span data-ttu-id="3b8b5-132">Выберите **Пространственный звук -> Windows Sonic для наушников** , чтобы получить представление о том, каким будет звучание в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-132">Choose **Spatial sound -> Windows Sonic for Headphones** to get the best representation of what you'll hear on HoloLens 2.</span></span>

![Подключаемый модуль пространственной обработки](images/unreal-spatial-audio-img-04.png)

> [!NOTE]
><span data-ttu-id="3b8b5-134">Этот параметр обязателен, только если вы планируете тестировать проект в Unreal Editor.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-134">This setting is only required if you plan to test your project in the Unreal editor.</span></span>

## <a name="creating-attenuation-objects"></a><span data-ttu-id="3b8b5-135">Создание объектов затухания</span><span class="sxs-lookup"><span data-stu-id="3b8b5-135">Creating Attenuation objects</span></span>
<span data-ttu-id="3b8b5-136">После установки и настройки необходимых подключаемых модулей выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="3b8b5-136">After you've installed and configured the necessary plugins:</span></span>
1. <span data-ttu-id="3b8b5-137">Выполните поиск актера **Ambient Sound** (Звуковое окружение) в окне **Place Actors** (Размещение актеров) и перетащите его в окно **Scene** (Сцена).</span><span class="sxs-lookup"><span data-stu-id="3b8b5-137">Search for an **Ambient Sound** actor in the **Place Actors** window and drag it into the **Scene** window.</span></span>

![Добавление актера звукового окружения](images/unreal-spatial-audio-img-07.png)

2. <span data-ttu-id="3b8b5-139">Сделайте актера **Ambient Sound** (Звуковое окружение) дочерним элементом визуального элемента в вашей сцене.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-139">Make the **Ambient Sound** actor a child of a visual element in your scene.</span></span>
    * <span data-ttu-id="3b8b5-140">По умолчанию актер Ambient Sound (Звуковое окружение) не имеет визуального представления, поэтому вы будете только слышать звук, поступающий из его расположения в сцене.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-140">An Ambient Sound actor doesn't have any visual representation by default, so you'll only hear a sound from its position in the scene.</span></span> <span data-ttu-id="3b8b5-141">Если вы присоедините его к визуальному элементу, вы сможете видеть и перемещать актер как любой другой ресурс.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-141">Attaching it to a visual element let's you see and move the actor like any other asset.</span></span>

3.  <span data-ttu-id="3b8b5-142">Щелкните правой кнопкой мыши в окне **Content Browser** (Обозреватель содержимого) и выберите **Create Advanced Asset -> Sounds -> Sound Attenuation** (Создать расширенный ресурс -> Звуки -> Затухание звука):</span><span class="sxs-lookup"><span data-stu-id="3b8b5-142">Right-click on the **Content Browser** and selecting **Create Advanced Asset -> Sounds -> Sound Attenuation** :</span></span>

![Создание ресурса затухания звука](images/unreal-spatial-audio-img-06.png)

4. <span data-ttu-id="3b8b5-144">Щелкните правой кнопкой мыши ресурс **Sound Attenuation** (Затухание звука) в окне **Content Browser** (Обозреватель содержимого) и выберите **Edit** (Правка), чтобы открыть окно свойств.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-144">Right-click on the **Sound Attenuation** asset in the **Content Browser** window and select the **Edit** option to bring up the properties window.</span></span>
    * <span data-ttu-id="3b8b5-145">Установите для параметра **Spatialization Method** (Метод пространственной обработки) значение **Binaural** (Стереофоническая).</span><span class="sxs-lookup"><span data-stu-id="3b8b5-145">Switch the **Spatialization Method** to **Binaural** .</span></span>

![Настройка метода пространственной обработки](images/unreal-spatial-audio-img-03.png)

5. <span data-ttu-id="3b8b5-147">Выберите актер **Ambient Sound** (Звуковое окружение) и прокрутите вниз до раздела **Attenuation** (Затухание) в области **Details** (Сведения).</span><span class="sxs-lookup"><span data-stu-id="3b8b5-147">Select the **Ambient Sound** actor and scroll down to the **Attenuation** section in the **Details** panel.</span></span>
    * <span data-ttu-id="3b8b5-148">Задайте для свойства **Attenuation Settings** (Параметры затухания) созданный вами ресурс **Sound Attenuation** (Затухание звука).</span><span class="sxs-lookup"><span data-stu-id="3b8b5-148">Set the **Attenuation Settings** property to the **Sound Attenuation** asset you created.</span></span>

![Настройка параметра затухания](images/unreal-spatial-audio-img-08.png)

6. <span data-ttu-id="3b8b5-150">Задайте объект **Sound Asset** (Звуковой ресурс), который вы хотите присоединить к актеру Ambient Sound (Звуковое окружение), указав для свойства **Sound** (Звук) этого актера файл SoundAsset.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-150">Set the **Sound Asset** you want to attach to the Ambient Sound actor by updating the **Sound** property of the Ambient Sound actor to specify the SoundAsset file to use.</span></span>

![Настройка звукового ресурса](images/unreal-spatial-audio-img-09.png)

> [!NOTE]
> <span data-ttu-id="3b8b5-152">Файл SoundAsset должен иметь монофонический формат, чтобы подключаемый модуль пространственного звука (Майкрософт) мог обработать его.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-152">The SoundAsset file needs to be mono to be spatialized with the Microsoft Spatial Sound plug-in.</span></span> <span data-ttu-id="3b8b5-153">Свойства звукового файла можно найти, наведя курсор на ресурс в окне Content Browser (Обозреватель содержимого), как показано на снимке экрана ниже.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-153">You can find the sound file properties by hovering over the asset in the Content Browser window as shown in the screenshot below.</span></span>

![Новый ресурс затухания звука](images/unreal-spatial-audio-img-10.png)

<span data-ttu-id="3b8b5-155">После настройки всех этих параметров для звукового окружения можно включить пространственную обработку с помощью выделенного оборудования HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-155">Once all of this is configured the ambient sound can be spatialized using the dedicated hardware offload support on HoloLens 2.</span></span>

## <a name="configuring-objects-for-spatialization"></a><span data-ttu-id="3b8b5-156">Настройка объектов для пространственной обработки</span><span class="sxs-lookup"><span data-stu-id="3b8b5-156">Configuring objects for spatialization</span></span>
<span data-ttu-id="3b8b5-157">Наличие пространственного звука означает, что вы управляете поведением звука в виртуальной среде.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-157">Working with spatial audio means you're in charge of managing how sound behaves in a virtual environment.</span></span> <span data-ttu-id="3b8b5-158">При создании звуковых объектов уделяйте внимание тому, чтобы их громкость повышалась при приближении пользователя и уменьшалась при отдалении.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-158">Your main focus is creating sound objects that appear louder when the user is close, and quieter when the user is far away.</span></span> <span data-ttu-id="3b8b5-159">Это называется затуханием звука — оно создает иллюзию того, что звук расположен в фиксированной точке.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-159">This is referred to as sound attenuation, making sounds appear as if they are positioned in a fixed spot.</span></span>

<span data-ttu-id="3b8b5-160">Для всех объектов затухания можно изменить такие параметры, как:</span><span class="sxs-lookup"><span data-stu-id="3b8b5-160">All attenuation objects come with modifiable settings for:</span></span>
* <span data-ttu-id="3b8b5-161">расстояние;</span><span class="sxs-lookup"><span data-stu-id="3b8b5-161">Distance</span></span>
* <span data-ttu-id="3b8b5-162">пространственная обработка;</span><span class="sxs-lookup"><span data-stu-id="3b8b5-162">Spatialization</span></span>
* <span data-ttu-id="3b8b5-163">абсорбция воздуха;</span><span class="sxs-lookup"><span data-stu-id="3b8b5-163">Air Absorption</span></span>
* <span data-ttu-id="3b8b5-164">фокус слушателя;</span><span class="sxs-lookup"><span data-stu-id="3b8b5-164">Listener Focus</span></span>
* <span data-ttu-id="3b8b5-165">отправка реверберации;</span><span class="sxs-lookup"><span data-stu-id="3b8b5-165">Reverb Send</span></span>
* <span data-ttu-id="3b8b5-166">Загораживание</span><span class="sxs-lookup"><span data-stu-id="3b8b5-166">Occlusion</span></span>

<span data-ttu-id="3b8b5-167">В статье [Затухание звука в Unreal](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html) приведены подробные сведения по каждой из этих тем.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-167">[Sound attenuation in Unreal](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html) has details and implementation specifics on each of these topics.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="3b8b5-168">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="3b8b5-168">Next Development Checkpoint</span></span>

<span data-ttu-id="3b8b5-169">Если вы следуете изложенным нами этапам разработки для Unreal, вы как раз прошли половину в изучении основных стандартных блоков MRTK.</span><span class="sxs-lookup"><span data-stu-id="3b8b5-169">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="3b8b5-170">Отсюда вы можете перейти к следующему стандартному блоку:</span><span class="sxs-lookup"><span data-stu-id="3b8b5-170">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3b8b5-171">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="3b8b5-171">Voice input</span></span>](unreal-voice-input.md)

<span data-ttu-id="3b8b5-172">Или перейдите к возможностям и API платформы смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="3b8b5-172">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3b8b5-173">Камера HoloLens</span><span class="sxs-lookup"><span data-stu-id="3b8b5-173">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="3b8b5-174">Вы можете в любой момент вернуться к [этапам разработки для Unreal](unreal-development-overview.md#2-core-building-blocks).</span><span class="sxs-lookup"><span data-stu-id="3b8b5-174">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>


## <a name="see-also"></a><span data-ttu-id="3b8b5-175">См. также статью</span><span class="sxs-lookup"><span data-stu-id="3b8b5-175">See also</span></span>
* [<span data-ttu-id="3b8b5-176">Пространственный звук</span><span class="sxs-lookup"><span data-stu-id="3b8b5-176">Spatial Sound</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-sound)
* [<span data-ttu-id="3b8b5-177">Проектирование пространственного звука</span><span class="sxs-lookup"><span data-stu-id="3b8b5-177">Spatial Sound Design</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)
* [<span data-ttu-id="3b8b5-178">220. Пространство в смешанной реальности: пространственный звук</span><span class="sxs-lookup"><span data-stu-id="3b8b5-178">MR Spatial 220: Spatial sound</span></span>](https://docs.microsoft.com/windows/mixed-reality/holograms-220)
