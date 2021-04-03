---
title: 101. HoloLens (1-го поколения). Основы — завершение проекта с использованием устройства
description: Для ознакомления с основами Windows Mixed Reality следуйте этому пошаговому руководству по созданию кода с помощью Unity, Visual Studio и HoloLens.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Смешанная реальность, Windows Mixed Reality, HoloLens, голограмма, Academy, учебник, HoloLens, Academy смешанной реальности, Unity, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, Windows 10
ms.openlocfilehash: 0ebfeb017271b7f98093a8ba6cac59dccae2a440
ms.sourcegitcommit: 3236abcba27335fe3d52e38423d2b265ca883355
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106269950"
---
# <a name="hololens-1st-gen-basics-101-complete-project-with-device"></a><span data-ttu-id="c9b9e-104">Основные сведения о HoloLens (1 Gen) 101: завершение проекта с устройством</span><span class="sxs-lookup"><span data-stu-id="c9b9e-104">HoloLens (1st gen) Basics 101: Complete project with device</span></span>

<br>

>[!IMPORTANT]
><span data-ttu-id="c9b9e-105">Учебники по смешанной реальности Academy были разработаны с учетом таких впечатляющих головных телефонов, как HoloLens (1-го поколения), Unity 2017 и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen), Unity 2017, and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c9b9e-106">Поэтому мы считаем, что важно оставить эти руководства для разработчиков, которые ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span> <span data-ttu-id="c9b9e-107">Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2, и могут быть несовместимы с более новыми версиями Unity.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2 and may not be compatible with newer versions of Unity.</span></span>  <span data-ttu-id="c9b9e-108">Они будут сохранены для работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c9b9e-109">Опубликован [новый цикл руководств](mrlearning-base.md) для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-109">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

<span data-ttu-id="c9b9e-110">В этом руководстве описывается полный проект, встроенный в Unity, демонстрирующий основные функции Windows Mixed Reality в HoloLens, включая [взгляд](../../../design/gaze-and-commit.md), [жесты](../../../design/gaze-and-commit.md#composite-gestures), [речевой ввод](../../../design/voice-input.md), [Пространственный звук](../../../design/spatial-sound.md) и [пространственное сопоставление](../../../design/spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="c9b9e-110">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](../../../design/gaze-and-commit.md), [gestures](../../../design/gaze-and-commit.md#composite-gestures), [voice input](../../../design/voice-input.md), [spatial sound](../../../design/spatial-sound.md) and [spatial mapping](../../../design/spatial-mapping.md).</span></span>

<span data-ttu-id="c9b9e-111">Выполнение руководства займет примерно 1 час.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-111">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="c9b9e-112">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="c9b9e-112">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c9b9e-113">Курс</span><span class="sxs-lookup"><span data-stu-id="c9b9e-113">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c9b9e-114"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c9b9e-114"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c9b9e-115"><a href="../../../discover/immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="c9b9e-115"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="c9b9e-116">101. Основы смешанной реальности: полный проект с использованием устройства</span><span class="sxs-lookup"><span data-stu-id="c9b9e-116">MR Basics 101: Complete project with device</span></span></td><td style="text-align: center;"> <span data-ttu-id="c9b9e-117">✔️</span><span class="sxs-lookup"><span data-stu-id="c9b9e-117">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="c9b9e-118">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="c9b9e-118">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="c9b9e-119">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="c9b9e-119">Prerequisites</span></span>

* <span data-ttu-id="c9b9e-120">КОМПЬЮТЕР с Windows 10, на котором [установлены правильные средства](../../install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="c9b9e-120">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md).</span></span>
* <span data-ttu-id="c9b9e-121">Устройство HoloLens, [настроенное для разработки](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="c9b9e-121">A HoloLens device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="c9b9e-122">Файлы проекта</span><span class="sxs-lookup"><span data-stu-id="c9b9e-122">Project files</span></span>

* <span data-ttu-id="c9b9e-123">Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) , необходимые для проекта.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-123">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span> <span data-ttu-id="c9b9e-124">Требуется Unity 2017,2 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-124">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="c9b9e-125">Если вам по-прежнему требуется поддержка Unity 5,6, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span><span class="sxs-lookup"><span data-stu-id="c9b9e-125">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="c9b9e-126">Если вам по-прежнему требуется поддержка Unity 5,5, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span><span class="sxs-lookup"><span data-stu-id="c9b9e-126">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="c9b9e-127">Если вам по-прежнему требуется поддержка Unity 5,4, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span><span class="sxs-lookup"><span data-stu-id="c9b9e-127">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="c9b9e-128">Отмена архивации файлов на Рабочий стол или другого места для удобства доступа.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-128">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="c9b9e-129">В качестве имени папки используйте **Origami**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-129">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="c9b9e-130">Если вы хотите просмотреть исходный код перед загрузкой, он [доступен на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span><span class="sxs-lookup"><span data-stu-id="c9b9e-130">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="c9b9e-131">Глава 1-"Холо"</span><span class="sxs-lookup"><span data-stu-id="c9b9e-131">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

<span data-ttu-id="c9b9e-132">В этой главе мы создадим наш первый проект Unity и пошаговым процессом сборки и развертывания.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-132">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="c9b9e-133">Задачи</span><span class="sxs-lookup"><span data-stu-id="c9b9e-133">Objectives</span></span>

* <span data-ttu-id="c9b9e-134">Настройка Unity для разработки с Holographic.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-134">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="c9b9e-135">Создайте голограмму.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-135">Make a hologram.</span></span>
* <span data-ttu-id="c9b9e-136">Ознакомьтесь с созданной голограммой.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-136">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="c9b9e-137">Инструкции</span><span class="sxs-lookup"><span data-stu-id="c9b9e-137">Instructions</span></span>

* <span data-ttu-id="c9b9e-138">Запустите Unity.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-138">Start Unity.</span></span>
* <span data-ttu-id="c9b9e-139">Выберите **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-139">Select **Open**.</span></span>
* <span data-ttu-id="c9b9e-140">Введите Location в качестве папки **Origami** , которая была отменена для архивации.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-140">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="c9b9e-141">Выберите **Origami** и щелкните **выбрать папку**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-141">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="c9b9e-142">Так как проект **Origami** не содержит сцены, сохраните пустую сцену по умолчанию в новом файле с помощью команды: **файл**  /  **сохранить сцену как**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-142">Since the **Origami** project does not contain a scene, save the empty default scene to a new file using: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="c9b9e-143">Назовите новую сцену **Origami** и нажмите кнопку **Save (сохранить** ).</span><span class="sxs-lookup"><span data-stu-id="c9b9e-143">Name the new scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-virtual-camera"></a><span data-ttu-id="c9b9e-144">Настройка основной виртуальной камеры</span><span class="sxs-lookup"><span data-stu-id="c9b9e-144">Setup the main virtual camera</span></span>

* <span data-ttu-id="c9b9e-145">На панели **Иерархия** выберите объект **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-145">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="c9b9e-146">В **инспекторе** задайте для его параметра «transform **» значение 0, 0,** 0.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-146">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="c9b9e-147">Найдите свойство **clear flags** и измените раскрывающийся список с **скибокс** на **сплошной цвет**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-147">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="c9b9e-148">Щелкните поле **Фон**, чтобы открыть палитру.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-148">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="c9b9e-149">Задайте для **R, G, B, and A** (Красный, зеленый, синий и альфа-компонент) значение **0**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-149">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="c9b9e-150">Настройка сцены</span><span class="sxs-lookup"><span data-stu-id="c9b9e-150">Setup the scene</span></span>

* <span data-ttu-id="c9b9e-151">На **панели Иерархия** щелкните **создать** и **создать пустой**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-151">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="c9b9e-152">Щелкните правой кнопкой мыши новый **GameObject** и выберите команду Переименовать.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-152">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="c9b9e-153">Переименуйте GameObject в **оригамиколлектион**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-153">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="c9b9e-154">В папке **голограмм** на панели проекта (разверните ресурсы и выберите голограммы или дважды щелкните папку голограммы на панели проекта):</span><span class="sxs-lookup"><span data-stu-id="c9b9e-154">From the **Holograms** folder in the Project Panel (expand Assets and select Holograms or double click the Holograms folder in the Project Panel):</span></span>
  * <span data-ttu-id="c9b9e-155">Перетащите **этап** в иерархию, чтобы он был дочерним элементом **оригамиколлектион**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-155">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="c9b9e-156">Перетащите **Sphere1** в иерархию, чтобы она была дочерней для **оригамиколлектион**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-156">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="c9b9e-157">Перетащите **Sphere2** в иерархию, чтобы она была дочерней для **оригамиколлектион**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-157">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="c9b9e-158">Щелкните правой кнопкой мыши **направленный объект Light** на **панели Иерархия** и выберите команду **Удалить**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-158">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="c9b9e-159">Перетащите **индикаторы** из папки **голограммы** в корневую папку **панели Иерархия**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-159">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="c9b9e-160">В **иерархии** выберите **оригамиколлектион**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-160">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="c9b9e-161">В **инспекторе** задайте для параметра Расположение преобразования значение **0,-0,5, 2,0**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-161">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="c9b9e-162">Нажмите кнопку **воспроизвести** в Unity, чтобы просмотреть голограммы.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-162">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="c9b9e-163">В окне предварительного просмотра должны отобразиться объекты Origami.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-163">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="c9b9e-164">Чтобы выйти из режима предварительного просмотра, нажмите кнопку **воспроизвести** еще раз.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-164">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="c9b9e-165">Экспорт проекта из Unity в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c9b9e-165">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="c9b9e-166">В Unity выберите **файл > параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-166">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="c9b9e-167">Выберите **универсальная платформа Windows** в списке **платформа** и щелкните **параметр платформа**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-167">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="c9b9e-168">Задайте для **пакета SDK** значение **универсальное 10** , а для **типа сборки** — **D3D**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-168">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="c9b9e-169">Проверьте **проекты C# для Unity**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-169">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="c9b9e-170">Щелкните **Добавить открытые сцены** , чтобы добавить сцену.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-170">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="c9b9e-171">Щелкните **Построить**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-171">Click **Build**.</span></span>
* <span data-ttu-id="c9b9e-172">В открывшемся окне проводника создайте **новую папку** с именем App.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-172">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="c9b9e-173">Щелкните **папку приложения** одним щелчком мыши.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-173">Single click the **App Folder**.</span></span>
* <span data-ttu-id="c9b9e-174">Нажмите кнопку **выбрать папку**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-174">Press **Select Folder**.</span></span>
* <span data-ttu-id="c9b9e-175">После завершения Unity появится окно проводника.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-175">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="c9b9e-176">Откройте папку **приложения** .</span><span class="sxs-lookup"><span data-stu-id="c9b9e-176">Open the **App** folder.</span></span>
* <span data-ttu-id="c9b9e-177">Откройте (дважды щелкните) **Origami. sln**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-177">Open (double click) **Origami.sln**.</span></span>
* <span data-ttu-id="c9b9e-178">С помощью верхней панели инструментов в Visual Studio измените целевой объект с отладка на **выпуск** и с ARM на **x86**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-178">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="c9b9e-179">Щелкните стрелку рядом с кнопкой устройство и выберите **Удаленный компьютер** для развертывания через Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-179">Click on the arrow next to the Device button, and select **Remote Machine** to deploy over Wi-Fi.</span></span>
  * <span data-ttu-id="c9b9e-180">Присвойте **адресу** имя или IP-адрес HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-180">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="c9b9e-181">Если вы не знакомы с IP-адресом устройства, проверьте **параметры > сеть & интернет > дополнительные параметры** или спросите Кортану **"Привет, Кортана," мой IP-адрес ".**</span><span class="sxs-lookup"><span data-stu-id="c9b9e-181">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
  * <span data-ttu-id="c9b9e-182">Если HoloLens подключен через USB, вы можете выбрать **устройство** для развертывания через USB.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-182">If the HoloLens is attached over USB, you may instead select **Device** to deploy over USB.</span></span>
  * <span data-ttu-id="c9b9e-183">Оставьте для параметра **режим проверки подлинности** значение **универсальное**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-183">Leave the **Authentication Mode** set to **Universal**.</span></span>
  * <span data-ttu-id="c9b9e-184">Нажмите кнопку **выбрать** .</span><span class="sxs-lookup"><span data-stu-id="c9b9e-184">Click **Select**</span></span>

* <span data-ttu-id="c9b9e-185">Щелкните **отладка > начать без отладки** или нажмите клавиши **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-185">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="c9b9e-186">Если вы впервые развертываете на устройстве, вам потребуется [связать его с Visual Studio](../../platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).</span><span class="sxs-lookup"><span data-stu-id="c9b9e-186">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](../../platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).</span></span>

* <span data-ttu-id="c9b9e-187">Теперь проект Origami будет строиться, развертываться в HoloLens, а затем выполнен.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-187">The Origami project will now build, deploy to your HoloLens, and then run.</span></span>
* <span data-ttu-id="c9b9e-188">Помещайтесь на HoloLens и проведите поиск, чтобы увидеть новые голограммы.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-188">Put on your HoloLens and look around to see your new holograms.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="c9b9e-189">Глава 2. взгляд</span><span class="sxs-lookup"><span data-stu-id="c9b9e-189">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

<span data-ttu-id="c9b9e-190">В этой главе мы будем познакомиться с первым из трех способов взаимодействия с голограммами — [Взгляните](../../../design/gaze-and-commit.md).</span><span class="sxs-lookup"><span data-stu-id="c9b9e-190">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](../../../design/gaze-and-commit.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="c9b9e-191">Задачи</span><span class="sxs-lookup"><span data-stu-id="c9b9e-191">Objectives</span></span>

* <span data-ttu-id="c9b9e-192">Визуализируйте взгляд с помощью курсора, заблокированного по всему миру.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-192">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="c9b9e-193">Инструкции</span><span class="sxs-lookup"><span data-stu-id="c9b9e-193">Instructions</span></span>

* <span data-ttu-id="c9b9e-194">Вернитесь к проекту Unity и закройте окно параметры сборки, если оно все еще открыто.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-194">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="c9b9e-195">Выберите папку **голограммы** на **панели проект**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-195">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="c9b9e-196">Перетащите объект **курсора** на **панель Иерархия** на корневом уровне.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-196">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="c9b9e-197">Дважды щелкните объект **курсора** , чтобы просмотреть его Подробнее.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-197">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="c9b9e-198">Щелкните правой кнопкой мыши папку **сценарии** на панели проект.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-198">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="c9b9e-199">Щелкните подменю **создать** .</span><span class="sxs-lookup"><span data-stu-id="c9b9e-199">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="c9b9e-200">Выберите **скрипт C#**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-200">Select **C# Script**.</span></span>
* <span data-ttu-id="c9b9e-201">Назовите сценарий **ворлдкурсор**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-201">Name the script **WorldCursor**.</span></span> <span data-ttu-id="c9b9e-202">Примечание. в имени учитывается регистр.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-202">Note: The name is case-sensitive.</span></span> <span data-ttu-id="c9b9e-203">Добавлять расширение CS не требуется.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-203">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="c9b9e-204">Выберите объект **курсора** на **панели Иерархия**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-204">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="c9b9e-205">Перетащите сценарий **ворлдкурсор** на **Панель инспектора**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-205">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="c9b9e-206">Дважды щелкните скрипт **ворлдкурсор** , чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-206">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="c9b9e-207">Скопируйте и вставьте этот код в **ворлдкурсор. CS** и **Сохраните все**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-207">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move the cursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* <span data-ttu-id="c9b9e-208">Перестройте приложение из **файла > параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-208">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="c9b9e-209">Вернитесь к решению Visual Studio, которое ранее использовалось для развертывания в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-209">Return to the Visual Studio solution previously used to deploy to your HoloLens.</span></span>
* <span data-ttu-id="c9b9e-210">При появлении запроса выберите "перезагрузить все".</span><span class="sxs-lookup"><span data-stu-id="c9b9e-210">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="c9b9e-211">Щелкните **Отладка-> начать без отладки** или нажмите клавиши **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-211">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="c9b9e-212">Теперь взгляните на сцену и обратите внимание на то, как курсор взаимодействует с формой объектов.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-212">Now look around the scene and notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="c9b9e-213">Глава 3 — жесты</span><span class="sxs-lookup"><span data-stu-id="c9b9e-213">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

<span data-ttu-id="c9b9e-214">В этой главе мы добавим поддержку [жестов](../../../design/gaze-and-commit.md#composite-gestures).</span><span class="sxs-lookup"><span data-stu-id="c9b9e-214">In this chapter, we'll add support for [gestures](../../../design/gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="c9b9e-215">Когда пользователь выбирает бумажную сферу, мы сделаем сферу, включив для нее функцию "сила притяжения" с помощью системы обработки физических модулей Unity.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-215">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="c9b9e-216">Задачи</span><span class="sxs-lookup"><span data-stu-id="c9b9e-216">Objectives</span></span>

* <span data-ttu-id="c9b9e-217">Контролируйте голограммы с помощью жеста выбора.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-217">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="c9b9e-218">Инструкции</span><span class="sxs-lookup"><span data-stu-id="c9b9e-218">Instructions</span></span>

<span data-ttu-id="c9b9e-219">Начнем с создания скрипта, который затем может обнаружить жест выбора.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-219">We'll start by creating a script then can detect the Select gesture.</span></span>

* <span data-ttu-id="c9b9e-220">В папке **Scripts** создайте скрипт с именем **газежестуреманажер**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-220">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="c9b9e-221">Перетащите скрипт **газежестуреманажер** на объект **оригамиколлектион** в иерархии.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-221">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="c9b9e-222">Откройте скрипт **газежестуреманажер** в Visual Studio и добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="c9b9e-222">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Awake()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* <span data-ttu-id="c9b9e-223">Создайте другой скрипт в папке Scripts с именем **сферекоммандс**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-223">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="c9b9e-224">Разверните объект **оригамиколлектион** в представлении иерархии.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-224">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="c9b9e-225">Перетащите скрипт **сферекоммандс** на объект **Sphere1** на панели Иерархия.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-225">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="c9b9e-226">Перетащите скрипт **сферекоммандс** на объект **Sphere2** на панели Иерархия.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-226">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="c9b9e-227">Откройте скрипт в Visual Studio для редактирования и замените код по умолчанию следующим:</span><span class="sxs-lookup"><span data-stu-id="c9b9e-227">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* <span data-ttu-id="c9b9e-228">Экспортируйте, создайте и разверните приложение в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-228">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="c9b9e-229">Взгляните на одну из шарик.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-229">Look at one of the spheres.</span></span>
* <span data-ttu-id="c9b9e-230">Выполните жест SELECT и посмотрите на поверхность, расположенную ниже.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-230">Perform the select gesture and watch the sphere drop onto the surface below.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="c9b9e-231">Глава 4-Voice</span><span class="sxs-lookup"><span data-stu-id="c9b9e-231">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

<span data-ttu-id="c9b9e-232">В этой главе мы добавим поддержку двух [голосовых команд](../../../design/voice-input.md): "сбросить мир", чтобы вернуть удаленные шарик к их исходному расположению и "удалить шар", чтобы сделать сферу.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-232">In this chapter, we'll add support for two [voice commands](../../../design/voice-input.md): "Reset world" to return the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="c9b9e-233">Задачи</span><span class="sxs-lookup"><span data-stu-id="c9b9e-233">Objectives</span></span>

* <span data-ttu-id="c9b9e-234">Добавление речевых команд, которые всегда прослушиваются в фоновом режиме.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-234">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="c9b9e-235">Создайте голограмму, которая реагирует на голосовую команду.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-235">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="c9b9e-236">Инструкции</span><span class="sxs-lookup"><span data-stu-id="c9b9e-236">Instructions</span></span>

* <span data-ttu-id="c9b9e-237">В папке **Scripts** создайте скрипт с именем **спичманажер**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-237">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="c9b9e-238">Перетащите скрипт **спичманажер** на объект **оригамиколлектион** в иерархии</span><span class="sxs-lookup"><span data-stu-id="c9b9e-238">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="c9b9e-239">Откройте скрипт **спичманажер** в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-239">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="c9b9e-240">Скопируйте и вставьте этот код в **спичманажер. CS** и **Сохраните все**:</span><span class="sxs-lookup"><span data-stu-id="c9b9e-240">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* <span data-ttu-id="c9b9e-241">Откройте скрипт **сферекоммандс** в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-241">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="c9b9e-242">Обновите скрипт для чтения следующим образом:</span><span class="sxs-lookup"><span data-stu-id="c9b9e-242">Update the script to read as follows:</span></span>

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* <span data-ttu-id="c9b9e-243">Экспортируйте, создайте и разверните приложение в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-243">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="c9b9e-244">Взгляните на одну из шарик и скажите «**Drop Sphere**».</span><span class="sxs-lookup"><span data-stu-id="c9b9e-244">Look at one of the spheres, and say "**Drop Sphere**".</span></span>
* <span data-ttu-id="c9b9e-245">Скажите «**сбросить мир**», чтобы вернуть их в исходное положение.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-245">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="c9b9e-246">Глава 5 — Пространственный звук</span><span class="sxs-lookup"><span data-stu-id="c9b9e-246">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

<span data-ttu-id="c9b9e-247">В этой главе мы добавим музыку в приложение, а затем активируем звуковые эффекты для определенных действий.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-247">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="c9b9e-248">Мы будем использовать [Пространственный звук](../../../design/spatial-sound.md) , чтобы дать звуковое сопровождение определенному месту в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-248">We'll be using [spatial sound](../../../design/spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="c9b9e-249">Задачи</span><span class="sxs-lookup"><span data-stu-id="c9b9e-249">Objectives</span></span>

* <span data-ttu-id="c9b9e-250">Прослушайте голограммы в своем мире.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-250">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="c9b9e-251">Инструкции</span><span class="sxs-lookup"><span data-stu-id="c9b9e-251">Instructions</span></span>

* <span data-ttu-id="c9b9e-252">В Unity выберите в верхнем меню **правка > параметры проекта > звук**</span><span class="sxs-lookup"><span data-stu-id="c9b9e-252">In Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="c9b9e-253">На панели инспектора с правой стороны найдите параметр **подключаемый модуль спатиализер** и выберите **MS хртф спатиализер**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-253">In the Inspector Panel on the right side, find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="c9b9e-254">Из папки **голограмм** на панели проекта перетащите объект **окружения** на объект **оригамиколлектион** на панели Иерархия.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-254">From the **Holograms** folder in the Project panel, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="c9b9e-255">Выберите **оригамиколлектион** и найдите компонент « **источник звука** » на панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-255">Select **OrigamiCollection** and find the **Audio Source** component in the Inspector panel.</span></span> <span data-ttu-id="c9b9e-256">Измените следующие свойства:</span><span class="sxs-lookup"><span data-stu-id="c9b9e-256">Change these properties:</span></span>
  * <span data-ttu-id="c9b9e-257">Проверьте свойство **спатиализе** .</span><span class="sxs-lookup"><span data-stu-id="c9b9e-257">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="c9b9e-258">Проверьте **Воспроизведение в спящем** режиме.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-258">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="c9b9e-259">Измените **пространственный переход** на **3D** , перетащив ползунок вправо.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-259">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span> <span data-ttu-id="c9b9e-260">При перемещении ползунка значение должно меняться с 0 на 1.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-260">The value should change from 0 to 1 when you move the slider.</span></span>
  * <span data-ttu-id="c9b9e-261">Проверьте свойство **Loop** .</span><span class="sxs-lookup"><span data-stu-id="c9b9e-261">Check the **Loop** property.</span></span>
  * <span data-ttu-id="c9b9e-262">Разверните **Параметры 3D Sound** и введите **0,1** для **уровня Doppler**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-262">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="c9b9e-263">Задайте для параметра **Volume роллофф** значение **логарифмической роллофф**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-263">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="c9b9e-264">Установите **Максимальное расстояние** равным **20**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-264">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="c9b9e-265">В папке **Scripts** создайте скрипт с именем **сфересаундс**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-265">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="c9b9e-266">Перетащите **сфересаундс** в объекты **Sphere1** и **Sphere2** в иерархии.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-266">Drag and drop **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="c9b9e-267">Откройте **сфересаундс** в Visual Studio, обновите следующий код и **Сохраните все**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-267">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* <span data-ttu-id="c9b9e-268">Сохраните скрипт и вернитесь в Unity.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-268">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="c9b9e-269">Экспортируйте, создайте и разверните приложение в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-269">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="c9b9e-270">Передвиньтесь ближе и дальше с этапа и перенесите его на сторону, чтобы услышать смену звуков.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-270">Move closer and further from the Stage and turn side-to-side to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="c9b9e-271">Глава 6-пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="c9b9e-271">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

<span data-ttu-id="c9b9e-272">Теперь мы будем использовать [пространственное сопоставление](../../../design/spatial-mapping.md) , чтобы поместить игровую доску на реальный объект в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-272">Now we are going to use [spatial mapping](../../../design/spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="c9b9e-273">Задачи</span><span class="sxs-lookup"><span data-stu-id="c9b9e-273">Objectives</span></span>

* <span data-ttu-id="c9b9e-274">Приведите реальный мир к виртуальному миру.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-274">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="c9b9e-275">Размещайте голограммы, где это важно.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-275">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="c9b9e-276">Инструкции</span><span class="sxs-lookup"><span data-stu-id="c9b9e-276">Instructions</span></span>

* <span data-ttu-id="c9b9e-277">В Unity щелкните папку **голограмм** на панели проект.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-277">In Unity, click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="c9b9e-278">Перетащите ресурс **пространственного сопоставления** в корень **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-278">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="c9b9e-279">Щелкните объект **пространственного сопоставления** в иерархии.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-279">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="c9b9e-280">На **панели инспектора** измените следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-280">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="c9b9e-281">Установите флажок **рисовать визуальные сетки** .</span><span class="sxs-lookup"><span data-stu-id="c9b9e-281">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="c9b9e-282">Перейдите на вкладку **Рисование материалов** и щелкните окружность справа.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-282">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="c9b9e-283">Введите "**каркасная** схема" в поле поиска вверху.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-283">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="c9b9e-284">Щелкните результат, а затем закройте окно.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-284">Click on the result and then close the window.</span></span> <span data-ttu-id="c9b9e-285">При этом значение для рисования материала должно быть установлено в каркас.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-285">When you do this, the value for Draw Material should get set to Wireframe.</span></span>
* <span data-ttu-id="c9b9e-286">Экспортируйте, создайте и разверните приложение в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-286">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="c9b9e-287">При запуске приложения в реальной среде будет накладываться каркасная сетка.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-287">When the app runs, a wireframe mesh will overlay your real world.</span></span>
* <span data-ttu-id="c9b9e-288">Следите за тем, как изкрутка будет выпадать за пределы этапа, и на этаж!</span><span class="sxs-lookup"><span data-stu-id="c9b9e-288">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="c9b9e-289">Теперь мы покажем, как переместить Оригамиколлектион в новое расположение:</span><span class="sxs-lookup"><span data-stu-id="c9b9e-289">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="c9b9e-290">В папке **Scripts** создайте скрипт с именем **таптоплацепарент**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-290">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="c9b9e-291">В **иерархии** разверните **оригамиколлектион** и выберите объект **Stage** .</span><span class="sxs-lookup"><span data-stu-id="c9b9e-291">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="c9b9e-292">Перетащите скрипт **таптоплацепарент** на объект Stage.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-292">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="c9b9e-293">Откройте скрипт **таптоплацепарент** в Visual Studio и обновите его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="c9b9e-293">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* <span data-ttu-id="c9b9e-294">Экспорт, сборка и развертывание приложения.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-294">Export, build and deploy the app.</span></span>
* <span data-ttu-id="c9b9e-295">Теперь вы можете разместить игру в определенном месте, облаками ее с помощью жеста SELECT, а затем переместить в новое место и снова с помощью жеста выбора.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-295">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="chapter-7---holographic-fun"></a><span data-ttu-id="c9b9e-296">Глава 7-holographic</span><span class="sxs-lookup"><span data-stu-id="c9b9e-296">Chapter 7 - Holographic fun</span></span>

### <a name="objectives"></a><span data-ttu-id="c9b9e-297">Задачи</span><span class="sxs-lookup"><span data-stu-id="c9b9e-297">Objectives</span></span>

* <span data-ttu-id="c9b9e-298">Показать вход в неограниченный мир.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-298">Reveal the entrance to a holographic underworld.</span></span>

### <a name="instructions"></a><span data-ttu-id="c9b9e-299">Инструкции</span><span class="sxs-lookup"><span data-stu-id="c9b9e-299">Instructions</span></span>

<span data-ttu-id="c9b9e-300">Теперь мы покажем, как открыть немалое время:</span><span class="sxs-lookup"><span data-stu-id="c9b9e-300">Now we'll show you how to uncover the holographic underworld:</span></span>

* <span data-ttu-id="c9b9e-301">Из папки **голограмм** на панели проекта:</span><span class="sxs-lookup"><span data-stu-id="c9b9e-301">From the **Holograms** folder in the Project Panel:</span></span>
  * <span data-ttu-id="c9b9e-302">Перетащите элемент " **подсветка мира** " в иерархию, чтобы он был дочерним элементом **оригамиколлектион**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-302">Drag **Underworld** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="c9b9e-303">В папке **Scripts** создайте скрипт с именем **хиттаржет**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-303">In the **Scripts** folder, create a script named **HitTarget**.</span></span>
* <span data-ttu-id="c9b9e-304">В **иерархии** разверните узел **оригамиколлектион**.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-304">In the **Hierarchy**, expand the **OrigamiCollection**.</span></span>
* <span data-ttu-id="c9b9e-305">Разверните объект **Stage** и выберите **целевой** объект (синий вентилятор).</span><span class="sxs-lookup"><span data-stu-id="c9b9e-305">Expand the **Stage** object and select the **Target** object (blue fan).</span></span>
* <span data-ttu-id="c9b9e-306">Перетащите скрипт **хиттаржет** на **целевой** объект.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-306">Drag the **HitTarget** script onto the **Target** object.</span></span>
* <span data-ttu-id="c9b9e-307">Откройте скрипт **хиттаржет** в Visual Studio и обновите его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="c9b9e-307">Open the **HitTarget** script in Visual Studio, and update it to be the following:</span></span>

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* <span data-ttu-id="c9b9e-308">В Unity выберите **целевой** объект.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-308">In Unity, select the **Target** object.</span></span>
* <span data-ttu-id="c9b9e-309">Два открытых свойства теперь видны на целевом компоненте для **попадания** и должны ссылаться на объекты в нашей сцене:</span><span class="sxs-lookup"><span data-stu-id="c9b9e-309">Two public properties are now visible on the **Hit Target** component and need to reference objects in our scene:</span></span>
  * <span data-ttu-id="c9b9e-310">Перетащите элемент « **подсветка мира** » с панели « **Иерархия** » в свойство «подсветка» для **целевого** компонента. </span><span class="sxs-lookup"><span data-stu-id="c9b9e-310">Drag **Underworld** from the **Hierarchy** panel to the **Underworld** property on the **Hit Target** component.</span></span>
  * <span data-ttu-id="c9b9e-311">Перетащите **этап** из панели **Иерархия** в **объект, чтобы скрыть** свойство в целевом компоненте для **попадания** .</span><span class="sxs-lookup"><span data-stu-id="c9b9e-311">Drag **Stage** from the **Hierarchy** panel to the **Object to Hide** property on the **Hit Target** component.</span></span>
* <span data-ttu-id="c9b9e-312">Экспорт, сборка и развертывание приложения.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-312">Export, build and deploy the app.</span></span>
* <span data-ttu-id="c9b9e-313">Поместите коллекцию Origami в этаж, а затем с помощью жеста выбора выполните перетаскивание сферы.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-313">Place the Origami Collection on the floor, and then use the Select gesture to make a sphere drop.</span></span>
* <span data-ttu-id="c9b9e-314">Когда сфера достигнет цели (синий вентилятор), произойдет развертывание.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-314">When the sphere hits the target (blue fan), an explosion will occur.</span></span> <span data-ttu-id="c9b9e-315">Коллекция будет скрыта, и появится отверстие для подсветки.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-315">The collection will be hidden and a hole to the underworld will appear.</span></span>

## <a name="the-end"></a><span data-ttu-id="c9b9e-316">Конец</span><span class="sxs-lookup"><span data-stu-id="c9b9e-316">The end</span></span>

<span data-ttu-id="c9b9e-317">И это окончание этого руководства.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-317">And that's the end of this tutorial!</span></span>

<span data-ttu-id="c9b9e-318">Вы узнали:</span><span class="sxs-lookup"><span data-stu-id="c9b9e-318">You learned:</span></span>

* <span data-ttu-id="c9b9e-319">Создание приложения holographic в Unity.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-319">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="c9b9e-320">Как использовать взгляд, жест, голосовое, звуковое и пространственное сопоставление.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-320">How to make use of gaze, gesture, voice, sound, and spatial mapping.</span></span>
* <span data-ttu-id="c9b9e-321">Как создать и развернуть приложение с помощью Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-321">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="c9b9e-322">Теперь вы готовы приступить к созданию собственного опыта.</span><span class="sxs-lookup"><span data-stu-id="c9b9e-322">You are now ready to start creating your own holographic experience!</span></span>

## <a name="see-also"></a><span data-ttu-id="c9b9e-323">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c9b9e-323">See also</span></span>

* [<span data-ttu-id="c9b9e-324">101E. Основы смешанной реальности: полный проект с использованием эмулятора</span><span class="sxs-lookup"><span data-stu-id="c9b9e-324">MR Basics 101E: Complete project with emulator</span></span>](holograms-101e.md)
* [<span data-ttu-id="c9b9e-325">Взгляд</span><span class="sxs-lookup"><span data-stu-id="c9b9e-325">Gaze</span></span>](../../../design/gaze-and-commit.md)
* [<span data-ttu-id="c9b9e-326">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="c9b9e-326">Head-gaze and commit</span></span>](../../../design/gaze-and-commit.md)
* [<span data-ttu-id="c9b9e-327">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="c9b9e-327">Voice input</span></span>](../../../design/voice-input.md)
* [<span data-ttu-id="c9b9e-328">Пространственный звук</span><span class="sxs-lookup"><span data-stu-id="c9b9e-328">Spatial sound</span></span>](../../../design/spatial-sound.md)
* [<span data-ttu-id="c9b9e-329">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="c9b9e-329">Spatial mapping</span></span>](../../../design/spatial-mapping.md)