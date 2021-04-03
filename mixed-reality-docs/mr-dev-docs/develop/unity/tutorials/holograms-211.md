---
title: 211. HoloLens (1-го поколения). Ввод — жест
description: Выполните приведенное ниже пошаговое руководство по программированию с помощью Unity, Visual Studio и HoloLens, чтобы узнать о концепциях жестов.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: холотулкит, микседреалититулкит, микседреалититулкит-Unity, Academy, руководство, жест, HoloLens, Mixed Reality, Unity, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, Windows 10
ms.openlocfilehash: 1431c9b53657e2cec1bd6ade1a3629e628e15917
ms.sourcegitcommit: 3236abcba27335fe3d52e38423d2b265ca883355
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106269990"
---
# <a name="hololens-1st-gen-input-211-gesture"></a><span data-ttu-id="65617-104">Входные данные HoloLens (1-го поколения) 211: жест</span><span class="sxs-lookup"><span data-stu-id="65617-104">HoloLens (1st gen) Input 211: Gesture</span></span>

>[!IMPORTANT]
><span data-ttu-id="65617-105">Учебники по смешанной реальности Academy были разработаны с учетом таких впечатляющих головных телефонов, как HoloLens (1-го поколения), Unity 2017 и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="65617-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen), Unity 2017, and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="65617-106">Поэтому мы считаем, что важно оставить эти руководства для разработчиков, которые ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="65617-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span> <span data-ttu-id="65617-107">Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2, и могут быть несовместимы с более новыми версиями Unity.</span><span class="sxs-lookup"><span data-stu-id="65617-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2 and may not be compatible with newer versions of Unity.</span></span>  <span data-ttu-id="65617-108">Они будут сохранены для работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="65617-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="65617-109">Опубликован [новый цикл руководств](mrlearning-base.md) для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="65617-109">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="65617-110">[Жесты](../../../design/gaze-and-commit.md#composite-gestures) применяют намерение пользователя к действию.</span><span class="sxs-lookup"><span data-stu-id="65617-110">[Gestures](../../../design/gaze-and-commit.md#composite-gestures) turn user intention into action.</span></span> <span data-ttu-id="65617-111">С помощью жестов пользователи могут взаимодействовать с голограммами.</span><span class="sxs-lookup"><span data-stu-id="65617-111">With gestures, users can interact with holograms.</span></span> <span data-ttu-id="65617-112">В этом курсе мы расскажем, как контролировать руки пользователя, реагировать на вводимые пользователем данные и предоставлять отзыв пользователю в зависимости от состояния и местоположения.</span><span class="sxs-lookup"><span data-stu-id="65617-112">In this course, we'll learn how to track the user's hands, respond to user input, and give feedback to the user based on hand state and location.</span></span>

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

<span data-ttu-id="65617-113">В статье об [основных принципах MR 101](../../../develop/unity/tutorials/holograms-101.md)мы использовали простой жест касания для взаимодействия с нашими голограммами.</span><span class="sxs-lookup"><span data-stu-id="65617-113">In [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md), we used a simple air-tap gesture to interact with our holograms.</span></span> <span data-ttu-id="65617-114">Теперь мы перейдем к жесту в области воздушного касания и изучим новые концепции:</span><span class="sxs-lookup"><span data-stu-id="65617-114">Now, we'll move beyond the air-tap gesture and explore new concepts to:</span></span>

* <span data-ttu-id="65617-115">Обнаружение времени трассировки пользователя и предоставление отзыва пользователю.</span><span class="sxs-lookup"><span data-stu-id="65617-115">Detect when the user's hand is being tracked and provide feedback to the user.</span></span>
* <span data-ttu-id="65617-116">Используйте жест навигации для поворота голограмм.</span><span class="sxs-lookup"><span data-stu-id="65617-116">Use a navigation gesture to rotate our holograms.</span></span>
* <span data-ttu-id="65617-117">Предоставьте отзыв о том, когда пользователь перейдет из режима руки.</span><span class="sxs-lookup"><span data-stu-id="65617-117">Provide feedback when the user's hand is about to go out of view.</span></span>
* <span data-ttu-id="65617-118">Используйте события манипуляции, чтобы позволить пользователям перемещать голограммы с помощью их руки.</span><span class="sxs-lookup"><span data-stu-id="65617-118">Use manipulation events to allow users to move holograms with their hands.</span></span>

<span data-ttu-id="65617-119">В этом курсе мы будем посещать **Обозреватель моделей** проектов Unity, который мы создали в [MR input 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="65617-119">In this course, we'll revisit the Unity project **Model Explorer**, which we built in [MR Input 210](holograms-210.md).</span></span> <span data-ttu-id="65617-120">Наш-космонавтамный дружественный подход назад поможет нам в исследовании новых концепций жестов.</span><span class="sxs-lookup"><span data-stu-id="65617-120">Our astronaut friend is back to assist us in our exploration of these new gesture concepts.</span></span>

>[!IMPORTANT]
><span data-ttu-id="65617-121">Видеоматериалы, внедренные в каждую из приведенных ниже глав, были записаны с использованием более старой версии Unity и набора средств Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="65617-121">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="65617-122">Хотя пошаговые инструкции являются точными и актуальными, в соответствующих видеоматериалах могут отображаться сценарии и визуальные элементы, которые являются неактуальными.</span><span class="sxs-lookup"><span data-stu-id="65617-122">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="65617-123">Видеоматериалы по-прежнему включены в постерити, так как эти концепции все еще применимы.</span><span class="sxs-lookup"><span data-stu-id="65617-123">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="65617-124">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="65617-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="65617-125">Курс</span><span class="sxs-lookup"><span data-stu-id="65617-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="65617-126"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="65617-126"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="65617-127"><a href="../../../discover/immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="65617-127"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="65617-128">211. Ввод в смешанной реальности: жесты</span><span class="sxs-lookup"><span data-stu-id="65617-128">MR Input 211: Gesture</span></span></td><td style="text-align: center;"> <span data-ttu-id="65617-129">✔️</span><span class="sxs-lookup"><span data-stu-id="65617-129">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="65617-130">✔️</span><span class="sxs-lookup"><span data-stu-id="65617-130">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="65617-131">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="65617-131">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="65617-132">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="65617-132">Prerequisites</span></span>

* <span data-ttu-id="65617-133">КОМПЬЮТЕР с Windows 10, на котором [установлены правильные средства](../../../develop/install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="65617-133">A Windows 10 PC configured with the correct [tools installed](../../../develop/install-the-tools.md).</span></span>
* <span data-ttu-id="65617-134">Некоторые основные возможности программирования на C#.</span><span class="sxs-lookup"><span data-stu-id="65617-134">Some basic C# programming ability.</span></span>
* <span data-ttu-id="65617-135">Вы должны были выполнить [Основные сведения о MR 101](../../../develop/unity/tutorials/holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="65617-135">You should have completed [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md).</span></span>
* <span data-ttu-id="65617-136">Необходимо завершить [Ввод MR 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="65617-136">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="65617-137">Устройство HoloLens, [настроенное для разработки](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="65617-137">A HoloLens device [configured for development](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="65617-138">Файлы проекта</span><span class="sxs-lookup"><span data-stu-id="65617-138">Project files</span></span>

* <span data-ttu-id="65617-139">Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) , необходимые для проекта.</span><span class="sxs-lookup"><span data-stu-id="65617-139">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) required by the project.</span></span> <span data-ttu-id="65617-140">Требуется Unity 2017,2 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="65617-140">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="65617-141">Отмена архивации файлов на Рабочий стол или другого места для удобства доступа.</span><span class="sxs-lookup"><span data-stu-id="65617-141">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="65617-142">Если вы хотите просмотреть исходный код перед загрузкой, он [доступен на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span><span class="sxs-lookup"><span data-stu-id="65617-142">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="65617-143">Ошибки и примечания</span><span class="sxs-lookup"><span data-stu-id="65617-143">Errata and Notes</span></span>

* <span data-ttu-id="65617-144">Параметр "Enable Только мой код" должен быть отключен (*снят*) в Visual Studio в разделе "сервис->параметры" — >Отладка для попадания в код точек останова в коде.</span><span class="sxs-lookup"><span data-stu-id="65617-144">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-0---unity-setup"></a><span data-ttu-id="65617-145">Глава 0-Установка Unity</span><span class="sxs-lookup"><span data-stu-id="65617-145">Chapter 0 - Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="65617-146">Инструкции</span><span class="sxs-lookup"><span data-stu-id="65617-146">Instructions</span></span>

1. <span data-ttu-id="65617-147">Запустите Unity.</span><span class="sxs-lookup"><span data-stu-id="65617-147">Start Unity.</span></span>
2. <span data-ttu-id="65617-148">Выберите **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="65617-148">Select **Open**.</span></span>
3. <span data-ttu-id="65617-149">Перейдите к папке **жестов** , для которой был отменен Архив.</span><span class="sxs-lookup"><span data-stu-id="65617-149">Navigate to the **Gesture** folder you previously un-archived.</span></span>
4. <span data-ttu-id="65617-150">Найдите и выберите **начальную** / папку **обозревателя моделей** .</span><span class="sxs-lookup"><span data-stu-id="65617-150">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="65617-151">Нажмите кнопку **выбрать папку** .</span><span class="sxs-lookup"><span data-stu-id="65617-151">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="65617-152">На панели **проект** разверните папку **сцены** .</span><span class="sxs-lookup"><span data-stu-id="65617-152">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="65617-153">Дважды щелкните **моделексплорер** сцену, чтобы загрузить его в Unity.</span><span class="sxs-lookup"><span data-stu-id="65617-153">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="65617-154">Сборка</span><span class="sxs-lookup"><span data-stu-id="65617-154">Building</span></span>

1. <span data-ttu-id="65617-155">В Unity выберите **файл > параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="65617-155">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="65617-156">Если « **сцены» или «моделексплорер** » в окне « **Построение**» не отображаются, щелкните **Добавить открытые сцены** , чтобы добавить сцену.</span><span class="sxs-lookup"><span data-stu-id="65617-156">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="65617-157">Если вы специально разрабатываете для HoloLens, задайте для параметра **целевое устройство** значение **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="65617-157">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="65617-158">В противном случае оставьте его на **любом устройстве**.</span><span class="sxs-lookup"><span data-stu-id="65617-158">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="65617-159">Убедитесь, что для **типа сборки** задано значение **D3D** и **пакет SDK** установлен в значение " **Последняя установленная версия** " (это должен быть пакет SDK 16299 или более поздней версии).</span><span class="sxs-lookup"><span data-stu-id="65617-159">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="65617-160">Щелкните **Построить**.</span><span class="sxs-lookup"><span data-stu-id="65617-160">Click **Build**.</span></span>
6. <span data-ttu-id="65617-161">Создайте **новую папку** с именем App.</span><span class="sxs-lookup"><span data-stu-id="65617-161">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="65617-162">Щелкните папку **приложения** одним щелчком мыши.</span><span class="sxs-lookup"><span data-stu-id="65617-162">Single click the **App** folder.</span></span>
8. <span data-ttu-id="65617-163">Нажмите кнопку **выбрать папку** , и Unity начнет создавать проект для Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="65617-163">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="65617-164">После завершения Unity появится окно проводника.</span><span class="sxs-lookup"><span data-stu-id="65617-164">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="65617-165">Откройте папку **приложения** .</span><span class="sxs-lookup"><span data-stu-id="65617-165">Open the **App** folder.</span></span>
2. <span data-ttu-id="65617-166">Откройте **решение Моделексплорер Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="65617-166">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="65617-167">При развертывании в HoloLens:</span><span class="sxs-lookup"><span data-stu-id="65617-167">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="65617-168">С помощью верхней панели инструментов в Visual Studio измените целевой объект с отладка на **выпуск** и с ARM на **x86**.</span><span class="sxs-lookup"><span data-stu-id="65617-168">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="65617-169">Щелкните стрелку раскрывающегося списка рядом с кнопкой локальный компьютер и выберите **Удаленный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="65617-169">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="65617-170">Введите **IP-адрес устройства HoloLens** и задайте для режима проверки подлинности значение **универсальный (незашифрованный протокол)**.</span><span class="sxs-lookup"><span data-stu-id="65617-170">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="65617-171">Нажмите кнопку **Выбрать**.</span><span class="sxs-lookup"><span data-stu-id="65617-171">Click **Select**.</span></span> <span data-ttu-id="65617-172">Если вы не узнаете IP-адрес устройства, проверьте **параметры > сеть & интернет > дополнительные параметры**.</span><span class="sxs-lookup"><span data-stu-id="65617-172">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="65617-173">В верхней строке меню щелкните **Отладка-> начать без отладки** или нажмите клавиши **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="65617-173">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="65617-174">Если вы впервые развертываете на устройстве, вам потребуется [связать его с Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).</span><span class="sxs-lookup"><span data-stu-id="65617-174">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).</span></span>
5. <span data-ttu-id="65617-175">После развертывания приложения закройте **фитбокс** с помощью **жеста выбора**.</span><span class="sxs-lookup"><span data-stu-id="65617-175">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="65617-176">При развертывании на иммерсивное головной телефон:</span><span class="sxs-lookup"><span data-stu-id="65617-176">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="65617-177">С помощью верхней панели инструментов в Visual Studio измените целевой объект с отладка на **выпуск** и с ARM на **x64**.</span><span class="sxs-lookup"><span data-stu-id="65617-177">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="65617-178">Убедитесь, что для целевого объекта развертывания задано значение **локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="65617-178">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="65617-179">В верхней строке меню щелкните **Отладка-> начать без отладки** или нажмите клавиши **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="65617-179">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="65617-180">После развертывания приложения закройте **фитбокс** , изменив триггер на контроллере движения.</span><span class="sxs-lookup"><span data-stu-id="65617-180">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="65617-181">Вы можете заметить некоторые красные ошибки на панели ошибок Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="65617-181">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="65617-182">Их можно спокойно игнорировать.</span><span class="sxs-lookup"><span data-stu-id="65617-182">It is safe to ignore them.</span></span> <span data-ttu-id="65617-183">Переключитесь на панель вывода для просмотра фактического хода построения.</span><span class="sxs-lookup"><span data-stu-id="65617-183">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="65617-184">Ошибки на панели вывода потребует внесения исправления (чаще всего они вызваны ошибкой в скрипте).</span><span class="sxs-lookup"><span data-stu-id="65617-184">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---hand-detected-feedback"></a><span data-ttu-id="65617-185">Глава 1. обнаружена обратная связь</span><span class="sxs-lookup"><span data-stu-id="65617-185">Chapter 1 - Hand detected feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a><span data-ttu-id="65617-186">Задачи</span><span class="sxs-lookup"><span data-stu-id="65617-186">Objectives</span></span>

* <span data-ttu-id="65617-187">Подпишитесь на события отслеживания.</span><span class="sxs-lookup"><span data-stu-id="65617-187">Subscribe to hand tracking events.</span></span>
* <span data-ttu-id="65617-188">Используйте обратную связь курсора для отображения пользователей при отслеживании руки.</span><span class="sxs-lookup"><span data-stu-id="65617-188">Use cursor feedback to show users when a hand is being tracked.</span></span>

>[!NOTE]
><span data-ttu-id="65617-189">В HoloLens 2 обнаруженные руки срабатывают каждый раз, когда видны руки (а не только при наведении указателя мыши на палец).</span><span class="sxs-lookup"><span data-stu-id="65617-189">On HoloLens 2 , hands detected fires whenever hands are visible (not just when a finger is pointing up).</span></span>

### <a name="instructions"></a><span data-ttu-id="65617-190">Инструкции</span><span class="sxs-lookup"><span data-stu-id="65617-190">Instructions</span></span>

* <span data-ttu-id="65617-191">На панели **Иерархия** разверните объект **InputManager** .</span><span class="sxs-lookup"><span data-stu-id="65617-191">In the **Hierarchy** panel, expand the **InputManager** object.</span></span>
* <span data-ttu-id="65617-192">Найдите и выберите объект **жестуресинпут** .</span><span class="sxs-lookup"><span data-stu-id="65617-192">Look for and select the **GesturesInput** object.</span></span>

<span data-ttu-id="65617-193">Сценарий **интерактионинпутсаурце. CS** выполняет следующие действия:</span><span class="sxs-lookup"><span data-stu-id="65617-193">The **InteractionInputSource.cs** script performs these steps:</span></span>

1. <span data-ttu-id="65617-194">Подписывается на события Интерактионсаурцедетектед и Интерактионсаурцелост.</span><span class="sxs-lookup"><span data-stu-id="65617-194">Subscribes to the InteractionSourceDetected and InteractionSourceLost events.</span></span>
2. <span data-ttu-id="65617-195">Задает состояние Ханддетектед.</span><span class="sxs-lookup"><span data-stu-id="65617-195">Sets the HandDetected state.</span></span>
3. <span data-ttu-id="65617-196">Отменяет подписывание событий Интерактионсаурцедетектед и Интерактионсаурцелост.</span><span class="sxs-lookup"><span data-stu-id="65617-196">Unsubscribes from the InteractionSourceDetected and InteractionSourceLost events.</span></span>

<span data-ttu-id="65617-197">Далее мы будем обновлять наш курсор с [MR Input 210](holograms-210.md) на тот, который отображает отзыв в зависимости от действий пользователя.</span><span class="sxs-lookup"><span data-stu-id="65617-197">Next, we'll upgrade our cursor from [MR Input 210](holograms-210.md) into one that shows feedback depending on the user's actions.</span></span>

1. <span data-ttu-id="65617-198">На панели **Иерархия** выберите объект **курсора** и удалите его.</span><span class="sxs-lookup"><span data-stu-id="65617-198">In the **Hierarchy** panel, select the **Cursor** object and delete it.</span></span>
2. <span data-ttu-id="65617-199">На панели **проект** найдите **курсорвисфидбакк** и перетащите его на панель **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="65617-199">In the **Project** panel, search for **CursorWithFeedback** and drag it into the **Hierarchy** panel.</span></span>
3. <span data-ttu-id="65617-200">Щелкните **InputManager** на панели **Иерархия** , а затем перетащите объект **Курсорвисфидбакк** из **иерархии** в поле **курсора** InputManager **симплесинглепоинтерселектор** в нижней части **инспектора**.</span><span class="sxs-lookup"><span data-stu-id="65617-200">Click on **InputManager** in the **Hierarchy** panel, then drag the **CursorWithFeedback** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>
4. <span data-ttu-id="65617-201">Щелкните **курсорвисфидбакк** в **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="65617-201">Click on the **CursorWithFeedback** in the **Hierarchy**.</span></span>
5. <span data-ttu-id="65617-202">На панели **инспектора** раскройте **данные о состоянии курсора** в скрипте **объект курсора** .</span><span class="sxs-lookup"><span data-stu-id="65617-202">In the **Inspector** panel, expand **Cursor State Data** on the **Object Cursor** script.</span></span>

<span data-ttu-id="65617-203">**Данные о состоянии курсора** работают следующим образом:</span><span class="sxs-lookup"><span data-stu-id="65617-203">The **Cursor State Data** works like this:</span></span>

* <span data-ttu-id="65617-204">Любое состояние **наблюдения** означает, что не обнаружена рука, и пользователь просто смотрит на экран.</span><span class="sxs-lookup"><span data-stu-id="65617-204">Any **Observe** state means that no hand is detected and the user is simply looking around.</span></span>
* <span data-ttu-id="65617-205">Любое состояние **взаимодействия** означает, что обнаружена рука или контроллер.</span><span class="sxs-lookup"><span data-stu-id="65617-205">Any **Interact** state means that a hand or controller is detected.</span></span>
* <span data-ttu-id="65617-206">Любое состояние **наведения указателя** означает, что пользователь смотрит на голограмму.</span><span class="sxs-lookup"><span data-stu-id="65617-206">Any **Hover** state means the user is looking at a hologram.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="65617-207">Построение и Развертывание</span><span class="sxs-lookup"><span data-stu-id="65617-207">Build and Deploy</span></span>

* <span data-ttu-id="65617-208">В Unity используйте **параметры сборки File >** для перестроения приложения.</span><span class="sxs-lookup"><span data-stu-id="65617-208">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="65617-209">Откройте папку **приложения** .</span><span class="sxs-lookup"><span data-stu-id="65617-209">Open the **App** folder.</span></span>
* <span data-ttu-id="65617-210">Откройте **решение Моделексплорер Visual Studio**, если оно еще не открыто.</span><span class="sxs-lookup"><span data-stu-id="65617-210">If it's not already open, open the **ModelExplorer Visual Studio Solution**.</span></span>
  * <span data-ttu-id="65617-211">(Если вы уже создали и развернули этот проект в Visual Studio во время настройки, то можете открыть этот экземпляр VS и нажать кнопку "перезагрузить все" при появлении соответствующего запроса).</span><span class="sxs-lookup"><span data-stu-id="65617-211">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>
* <span data-ttu-id="65617-212">В Visual Studio щелкните **Отладка-> начать без отладки** или нажмите клавиши **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="65617-212">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="65617-213">После развертывания приложения в HoloLens закройте фитбокс с помощью жеста касания.</span><span class="sxs-lookup"><span data-stu-id="65617-213">After the application deploys to the HoloLens, dismiss the fitbox using the air-tap gesture.</span></span>
* <span data-ttu-id="65617-214">Переместите руку в режим просмотра и наведите указатель пальца на положение "небесно", чтобы начать отслеживание.</span><span class="sxs-lookup"><span data-stu-id="65617-214">Move your hand into view and point your index finger to the sky to start hand tracking.</span></span>
* <span data-ttu-id="65617-215">Переместите руку влево, вправо, вверх и вниз.</span><span class="sxs-lookup"><span data-stu-id="65617-215">Move your hand left, right, up and down.</span></span>
* <span data-ttu-id="65617-216">Посмотрите, как меняется вид курсора при обнаружении и утере руки.</span><span class="sxs-lookup"><span data-stu-id="65617-216">Watch how the cursor changes when your hand is detected and then lost from view.</span></span>
* <span data-ttu-id="65617-217">Если вы используете иммерсивное головной телефон, вам потребуется подключиться к контроллеру и отключить его.</span><span class="sxs-lookup"><span data-stu-id="65617-217">If you're on an immersive headset, you'll have to connect and disconnect your controller.</span></span> <span data-ttu-id="65617-218">Этот отзыв становится менее интересным на иммерсивное устройство, так как подключенный контроллер всегда будет "доступен".</span><span class="sxs-lookup"><span data-stu-id="65617-218">This feedback becomes less interesting on an immersive device, as a connected controller will always be "available".</span></span>

## <a name="chapter-2---navigation"></a><span data-ttu-id="65617-219">Глава 2. Навигация</span><span class="sxs-lookup"><span data-stu-id="65617-219">Chapter 2 - Navigation</span></span>

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a><span data-ttu-id="65617-220">Задачи</span><span class="sxs-lookup"><span data-stu-id="65617-220">Objectives</span></span>

* <span data-ttu-id="65617-221">Используйте события жестов навигации для вращения-космонавтам.</span><span class="sxs-lookup"><span data-stu-id="65617-221">Use Navigation gesture events to rotate the astronaut.</span></span>

### <a name="instructions"></a><span data-ttu-id="65617-222">Инструкции</span><span class="sxs-lookup"><span data-stu-id="65617-222">Instructions</span></span>

<span data-ttu-id="65617-223">Чтобы использовать жесты навигации в нашем приложении, мы собираемся изменить **жестуреактион. CS** для поворота объектов при появлении жеста навигации.</span><span class="sxs-lookup"><span data-stu-id="65617-223">To use Navigation gestures in our app, we are going to edit **GestureAction.cs** to rotate objects when the Navigation gesture occurs.</span></span> <span data-ttu-id="65617-224">Кроме того, мы добавим отзыв к курсору, который будет отображаться, когда доступна Навигация.</span><span class="sxs-lookup"><span data-stu-id="65617-224">Additionally, we'll add feedback to the cursor to display when Navigation is available.</span></span>

1. <span data-ttu-id="65617-225">На панели **Иерархия** разверните узел **курсорвисфидбакк**.</span><span class="sxs-lookup"><span data-stu-id="65617-225">In the **Hierarchy** panel, expand **CursorWithFeedback**.</span></span>
2. <span data-ttu-id="65617-226">В папке **голограмм** найдите ресурс **скроллфидбакк** .</span><span class="sxs-lookup"><span data-stu-id="65617-226">In the **Holograms** folder, find the **ScrollFeedback** asset.</span></span>
3. <span data-ttu-id="65617-227">Перетащите **скроллфидбакк** prefab на **Курсорвисфидбакк** GameObject в **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="65617-227">Drag and drop the **ScrollFeedback** prefab onto the **CursorWithFeedback** GameObject in the **Hierarchy**.</span></span>
4. <span data-ttu-id="65617-228">Щелкните **курсорвисфидбакк**.</span><span class="sxs-lookup"><span data-stu-id="65617-228">Click on **CursorWithFeedback**.</span></span>
5. <span data-ttu-id="65617-229">На панели **инспектора** нажмите кнопку **Добавить компонент** .</span><span class="sxs-lookup"><span data-stu-id="65617-229">In the **Inspector** panel, click the **Add Component** button.</span></span>
6. <span data-ttu-id="65617-230">В меню введите **курсорфидбакк** в поле поиска.</span><span class="sxs-lookup"><span data-stu-id="65617-230">In the menu, type in the search box **CursorFeedback**.</span></span> <span data-ttu-id="65617-231">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="65617-231">Select the search result.</span></span>
7. <span data-ttu-id="65617-232">Перетащите объект **скроллфидбакк** из **иерархии** в свойство игровое поле, **обнаруженное прокруткой** в окне " **отзыв курсора** " в **инспекторе**.</span><span class="sxs-lookup"><span data-stu-id="65617-232">Drag and drop the **ScrollFeedback** object from the **Hierarchy** onto the **Scroll Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>
8. <span data-ttu-id="65617-233">На панели **Иерархия** выберите объект **астроман** .</span><span class="sxs-lookup"><span data-stu-id="65617-233">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
9. <span data-ttu-id="65617-234">На панели **инспектора** нажмите кнопку **Добавить компонент** .</span><span class="sxs-lookup"><span data-stu-id="65617-234">In the **Inspector** panel, click the **Add Component** button.</span></span>
10. <span data-ttu-id="65617-235">В меню введите **действие жеста** поля поиска.</span><span class="sxs-lookup"><span data-stu-id="65617-235">In the menu, type in the search box **Gesture Action**.</span></span> <span data-ttu-id="65617-236">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="65617-236">Select the search result.</span></span>

<span data-ttu-id="65617-237">Затем откройте **жестуреактион. CS** в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="65617-237">Next, open **GestureAction.cs** in Visual Studio.</span></span> <span data-ttu-id="65617-238">В написании упражнения 2. c измените сценарий, чтобы сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="65617-238">In coding exercise 2.c, edit the script to do the following:</span></span>

1. <span data-ttu-id="65617-239">**Поворот объекта астроман** при выполнении жеста навигации.</span><span class="sxs-lookup"><span data-stu-id="65617-239">**Rotate the AstroMan** object whenever a Navigation gesture is performed.</span></span>
2. <span data-ttu-id="65617-240">Вычислите **ротатионфактор** , чтобы управлять объемом вращения, применяемого к объекту.</span><span class="sxs-lookup"><span data-stu-id="65617-240">Calculate the **rotationFactor** to control the amount of rotation applied to the object.</span></span>
3. <span data-ttu-id="65617-241">**Поворот объекта** вокруг оси y, когда пользователь перемещает руку влево или вправо.</span><span class="sxs-lookup"><span data-stu-id="65617-241">**Rotate the object** around the y-axis when the user moves their hand left or right.</span></span>

<span data-ttu-id="65617-242">Выполните кодирование упражнений 2. c в скрипте или замените код завершенным решением ниже:</span><span class="sxs-lookup"><span data-stu-id="65617-242">Complete coding exercises 2.c in the script, or replace the code with the completed solution below:</span></span>

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

<span data-ttu-id="65617-243">Вы заметите, что другие события навигации уже заполнены некоторыми сведениями.</span><span class="sxs-lookup"><span data-stu-id="65617-243">You'll notice that the other navigation events are already filled in with some info.</span></span> <span data-ttu-id="65617-244">Мы принудительно GameObject в модальный стек Инпутсистем'с в наборе, поэтому пользователю не нужно поддерживать фокус на-космонавтам после начала вращения.</span><span class="sxs-lookup"><span data-stu-id="65617-244">We push the GameObject onto the Toolkit's InputSystem's modal stack, so the user doesn't have to maintain focus on the Astronaut once rotation has begun.</span></span> <span data-ttu-id="65617-245">Соответственно, при завершении жеста GameObjectся из стека.</span><span class="sxs-lookup"><span data-stu-id="65617-245">Correspondingly, we pop the GameObject off the stack once the gesture is completed.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="65617-246">Построение и Развертывание</span><span class="sxs-lookup"><span data-stu-id="65617-246">Build and Deploy</span></span>

1. <span data-ttu-id="65617-247">Перестройте приложение в Unity, а затем выполните сборку и развертывание из Visual Studio, чтобы запустить его в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="65617-247">Rebuild the application in Unity and then build and deploy from Visual Studio to run it in the HoloLens.</span></span>
2. <span data-ttu-id="65617-248">Взгляните на-космонавтам, на обеих сторонах курсора должны появиться две стрелки.</span><span class="sxs-lookup"><span data-stu-id="65617-248">Gaze at the astronaut, two arrows should appear on either side of the cursor.</span></span> <span data-ttu-id="65617-249">Этот новый визуальный элемент означает, что-космонавтам можно поворачивать.</span><span class="sxs-lookup"><span data-stu-id="65617-249">This new visual indicates that the astronaut can be rotated.</span></span>
3. <span data-ttu-id="65617-250">Поместите руку в готовую позицию (указатель пальца, указывающий на перевозки), чтобы HoloLens начал отслеживать свою руку.</span><span class="sxs-lookup"><span data-stu-id="65617-250">Place your hand in the ready position (index finger pointed towards the sky) so the HoloLens will start tracking your hand.</span></span>
4. <span data-ttu-id="65617-251">Чтобы повернуть-космонавтам, уменьшите индекс пальца до позиции сжатия, а затем переместите руку влево или вправо, чтобы активировать жест Навигатионкс.</span><span class="sxs-lookup"><span data-stu-id="65617-251">To rotate the astronaut, lower your index finger to a pinch position, and then move your hand left or right to trigger the NavigationX gesture.</span></span>

## <a name="chapter-3---hand-guidance"></a><span data-ttu-id="65617-252">Глава 3. Руководство по использованию</span><span class="sxs-lookup"><span data-stu-id="65617-252">Chapter 3 - Hand Guidance</span></span>

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a><span data-ttu-id="65617-253">Задачи</span><span class="sxs-lookup"><span data-stu-id="65617-253">Objectives</span></span>

* <span data-ttu-id="65617-254">Используйте **оценку руководства** для прогнозирования того, что отслеживание будет потеряно.</span><span class="sxs-lookup"><span data-stu-id="65617-254">Use **hand guidance score** to help predict when hand tracking will be lost.</span></span>
* <span data-ttu-id="65617-255">Оставить **отзыв о курсоре** , чтобы показать, когда рука пользователя приближается к границе представления.</span><span class="sxs-lookup"><span data-stu-id="65617-255">Provide **feedback on the cursor** to show when the user's hand nears the camera's edge of view.</span></span>

### <a name="instructions"></a><span data-ttu-id="65617-256">Инструкции</span><span class="sxs-lookup"><span data-stu-id="65617-256">Instructions</span></span>

1. <span data-ttu-id="65617-257">На панели **Иерархия** выберите объект **курсорвисфидбакк** .</span><span class="sxs-lookup"><span data-stu-id="65617-257">In the **Hierarchy** panel, select the **CursorWithFeedback** object.</span></span>
2. <span data-ttu-id="65617-258">На панели **инспектора** нажмите кнопку **Добавить компонент** .</span><span class="sxs-lookup"><span data-stu-id="65617-258">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="65617-259">В меню введите в поле **поиска.**</span><span class="sxs-lookup"><span data-stu-id="65617-259">In the menu, type in the search box **Hand Guidance**.</span></span> <span data-ttu-id="65617-260">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="65617-260">Select the search result.</span></span>
4. <span data-ttu-id="65617-261">В папке **голограммы** на панели **проекта** найдите ресурс **хандгуиданцефидбакк** .</span><span class="sxs-lookup"><span data-stu-id="65617-261">In the **Project** panel **Holograms** folder, find the **HandGuidanceFeedback** asset.</span></span>
5. <span data-ttu-id="65617-262">Перетащите ресурс **хандгуиданцефидбакк** в свойство **индикатор "рука** " на панели **инспектора** .</span><span class="sxs-lookup"><span data-stu-id="65617-262">Drag and drop the **HandGuidanceFeedback** asset onto the **Hand Guidance Indicator** property in the **Inspector** panel.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="65617-263">Построение и Развертывание</span><span class="sxs-lookup"><span data-stu-id="65617-263">Build and Deploy</span></span>

* <span data-ttu-id="65617-264">Перестройте приложение в Unity, а затем выполните сборку и развертывание из Visual Studio для работы с приложением в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="65617-264">Rebuild the application in Unity and then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="65617-265">Перенесите руку, чтобы просмотреть и подать указатель на палец.</span><span class="sxs-lookup"><span data-stu-id="65617-265">Bring your hand into view and raise your index finger to get tracked.</span></span>
* <span data-ttu-id="65617-266">Начните вращение-космонавтам с помощью жеста навигации (сжатие индекса и палец вместе).</span><span class="sxs-lookup"><span data-stu-id="65617-266">Start rotating the astronaut with the Navigation gesture (pinch your index finger and thumb together).</span></span>
* <span data-ttu-id="65617-267">Переместите руку налево, вправо, вверх и вниз.</span><span class="sxs-lookup"><span data-stu-id="65617-267">Move your hand far left, right, up, and down.</span></span>
* <span data-ttu-id="65617-268">По мере того, как приближается граница рамки жеста, рядом с курсором должна появиться стрелка, чтобы предупредить, что отслеживание будет потеряно.</span><span class="sxs-lookup"><span data-stu-id="65617-268">As your hand nears the edge of the gesture frame, an arrow should appear next to the cursor to warn you that hand tracking will be lost.</span></span> <span data-ttu-id="65617-269">Стрелка указывает направление движения руки, чтобы предотвратить потерю отслеживания.</span><span class="sxs-lookup"><span data-stu-id="65617-269">The arrow indicates which direction to move your hand in order to prevent tracking from being lost.</span></span>

## <a name="chapter-4---manipulation"></a><span data-ttu-id="65617-270">Глава 4. Управление</span><span class="sxs-lookup"><span data-stu-id="65617-270">Chapter 4 - Manipulation</span></span>

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a><span data-ttu-id="65617-271">Задачи</span><span class="sxs-lookup"><span data-stu-id="65617-271">Objectives</span></span>

* <span data-ttu-id="65617-272">Используйте события манипуляции для перемещения-космонавтам с помощью стрелок.</span><span class="sxs-lookup"><span data-stu-id="65617-272">Use Manipulation events to move the astronaut with your hands.</span></span>
* <span data-ttu-id="65617-273">Предоставьте отзыв о курсоре, чтобы пользователь мог понять, когда можно использовать манипуляцию.</span><span class="sxs-lookup"><span data-stu-id="65617-273">Provide feedback on the cursor to let the user know when Manipulation can be used.</span></span>

### <a name="instructions"></a><span data-ttu-id="65617-274">Инструкции</span><span class="sxs-lookup"><span data-stu-id="65617-274">Instructions</span></span>

<span data-ttu-id="65617-275">Жестуреманажер. cs и Астронаутманажер. CS позволяют нам выполнять следующие действия:</span><span class="sxs-lookup"><span data-stu-id="65617-275">GestureManager.cs and AstronautManager.cs will allow us to do the following:</span></span>

1. <span data-ttu-id="65617-276">Используйте ключевое слово "**Move-космонавтам**" для распознавания речи, чтобы включить жесты **манипуляции** и "**повернуть-космонавтам**", чтобы отключить их.</span><span class="sxs-lookup"><span data-stu-id="65617-276">Use the speech keyword "**Move Astronaut**" to enable **Manipulation** gestures and "**Rotate Astronaut**" to disable them.</span></span>
2. <span data-ttu-id="65617-277">Переключитесь на реакцию **распознавателя жестов манипуляции**.</span><span class="sxs-lookup"><span data-stu-id="65617-277">Switch to responding to the **Manipulation Gesture Recognizer**.</span></span>

<span data-ttu-id="65617-278">Давайте приступим.</span><span class="sxs-lookup"><span data-stu-id="65617-278">Let's get started.</span></span>

1. <span data-ttu-id="65617-279">На панели **Иерархия** создайте новый пустой GameObject.</span><span class="sxs-lookup"><span data-stu-id="65617-279">In the **Hierarchy** panel, create a new empty GameObject.</span></span> <span data-ttu-id="65617-280">Назовите его "**астронаутманажер**".</span><span class="sxs-lookup"><span data-stu-id="65617-280">Name it "**AstronautManager**".</span></span>
2. <span data-ttu-id="65617-281">На панели **инспектора** нажмите кнопку **Добавить компонент** .</span><span class="sxs-lookup"><span data-stu-id="65617-281">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="65617-282">В меню введите **-космонавтам Manager** в поле поиска.</span><span class="sxs-lookup"><span data-stu-id="65617-282">In the menu, type in the search box **Astronaut Manager**.</span></span> <span data-ttu-id="65617-283">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="65617-283">Select the search result.</span></span>
4. <span data-ttu-id="65617-284">На панели **инспектора** нажмите кнопку **Добавить компонент** .</span><span class="sxs-lookup"><span data-stu-id="65617-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
5. <span data-ttu-id="65617-285">В меню введите в поле поиска **речевой вход источник**.</span><span class="sxs-lookup"><span data-stu-id="65617-285">In the menu, type in the search box **Speech Input Source**.</span></span> <span data-ttu-id="65617-286">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="65617-286">Select the search result.</span></span>

<span data-ttu-id="65617-287">Теперь мы добавим речевые команды, необходимые для управления состоянием взаимодействия-космонавтам.</span><span class="sxs-lookup"><span data-stu-id="65617-287">We'll now add the speech commands required to control the interaction state of the astronaut.</span></span>

1. <span data-ttu-id="65617-288">Разверните раздел **Ключевые слова** в **инспекторе**.</span><span class="sxs-lookup"><span data-stu-id="65617-288">Expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="65617-289">Щелкните в **+** правой части, чтобы добавить новое ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="65617-289">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="65617-290">Введите ключевое слово как **Move-космонавтам**.</span><span class="sxs-lookup"><span data-stu-id="65617-290">Type the Keyword as **Move Astronaut**.</span></span> <span data-ttu-id="65617-291">При необходимости вы можете добавить сочетание клавиш.</span><span class="sxs-lookup"><span data-stu-id="65617-291">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="65617-292">Щелкните в **+** правой части, чтобы добавить новое ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="65617-292">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="65617-293">Введите ключевое слово " **повернуть-космонавтам**".</span><span class="sxs-lookup"><span data-stu-id="65617-293">Type the Keyword as **Rotate Astronaut**.</span></span> <span data-ttu-id="65617-294">При необходимости вы можете добавить сочетание клавиш.</span><span class="sxs-lookup"><span data-stu-id="65617-294">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="65617-295">Соответствующий код обработчика можно найти в **жестуреактион. CS** в обработчике **испичхандлер. онспичкэйвордрекогнизед** .</span><span class="sxs-lookup"><span data-stu-id="65617-295">The corresponding handler code can be found in **GestureAction.cs**, in the **ISpeechHandler.OnSpeechKeywordRecognized** handler.</span></span>

![Настройка источника речевого ввода в главе 4](images/holograms211-speech.png)

<span data-ttu-id="65617-297">Далее мы назовем обратную связь по манипуляции с курсором.</span><span class="sxs-lookup"><span data-stu-id="65617-297">Next, we'll setup the manipulation feedback on the cursor.</span></span>

1. <span data-ttu-id="65617-298">В папке **голограммы** на панели **проекта** найдите ресурс **пасингфидбакк** .</span><span class="sxs-lookup"><span data-stu-id="65617-298">In the **Project** panel **Holograms** folder, find the **PathingFeedback** asset.</span></span>
2. <span data-ttu-id="65617-299">Перетащите **пасингфидбакк** prefab на объект **курсорвисфидбакк** в **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="65617-299">Drag and drop the **PathingFeedback** prefab onto the **CursorWithFeedback** object in the **Hierarchy**.</span></span>
3. <span data-ttu-id="65617-300">На панели **Иерархия** щелкните **курсорвисфидбакк**.</span><span class="sxs-lookup"><span data-stu-id="65617-300">In the **Hierarchy** panel, click on **CursorWithFeedback**.</span></span>
4. <span data-ttu-id="65617-301">Перетащите объект **пасингфидбакк** из **иерархии** на обнаруженное пользователем свойство **игрового объекта** в компоненте **обратной связи** в **инспекторе**.</span><span class="sxs-lookup"><span data-stu-id="65617-301">Drag and drop the **PathingFeedback** object from the **Hierarchy** onto the **Pathing Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>

<span data-ttu-id="65617-302">Теперь необходимо добавить код в **жестуреактион. CS** , чтобы включить следующие возможности:</span><span class="sxs-lookup"><span data-stu-id="65617-302">Now we need to add code to **GestureAction.cs** to enable the following:</span></span>

1. <span data-ttu-id="65617-303">Добавьте код в функцию **иманипулатионхандлер. онманипулатионупдатед** , которая переместит-космонавтам при обнаружении жеста **манипуляции** .</span><span class="sxs-lookup"><span data-stu-id="65617-303">Add code to the **IManipulationHandler.OnManipulationUpdated** function, which will move the astronaut when a **Manipulation** gesture is detected.</span></span>
2. <span data-ttu-id="65617-304">Вычислите **вектор перемещения** , чтобы определить, куда следует переместить-космонавтам в зависимости от положения.</span><span class="sxs-lookup"><span data-stu-id="65617-304">Calculate the **movement vector** to determine where the astronaut should be moved to based on hand position.</span></span>
3. <span data-ttu-id="65617-305">**Переместите** -космонавтам в новое положение.</span><span class="sxs-lookup"><span data-stu-id="65617-305">**Move** the astronaut to the new position.</span></span>

<span data-ttu-id="65617-306">Завершите написание упражнения 4. a в **жестуреактион. CS** или используйте наше завершенное решение ниже:</span><span class="sxs-lookup"><span data-stu-id="65617-306">Complete coding exercise 4.a in **GestureAction.cs**, or use our completed solution below:</span></span>

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a><span data-ttu-id="65617-307">Построение и Развертывание</span><span class="sxs-lookup"><span data-stu-id="65617-307">Build and Deploy</span></span>

* <span data-ttu-id="65617-308">Перестройте в Unity, а затем выполните сборку и развертывание из Visual Studio, чтобы запустить приложение в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="65617-308">Rebuild in Unity and then build and deploy from Visual Studio to run the app in HoloLens.</span></span>
* <span data-ttu-id="65617-309">Переместите руку перед HoloLens и поднимите палец указателя, чтобы его можно было относить.</span><span class="sxs-lookup"><span data-stu-id="65617-309">Move your hand in front of the HoloLens and raise your index finger so that it can be tracked.</span></span>
* <span data-ttu-id="65617-310">Сосредоточьте курсор на-космонавтам.</span><span class="sxs-lookup"><span data-stu-id="65617-310">Focus the cursor over the astronaut.</span></span>
* <span data-ttu-id="65617-311">Скажите "Move-космонавтам", чтобы переместить-космонавтам с помощью жеста манипуляции.</span><span class="sxs-lookup"><span data-stu-id="65617-311">Say 'Move Astronaut' to move the astronaut with a Manipulation gesture.</span></span>
* <span data-ttu-id="65617-312">Вокруг курсора должны появиться четыре стрелки, чтобы показать, что программа будет реагировать на события манипуляции.</span><span class="sxs-lookup"><span data-stu-id="65617-312">Four arrows should appear around the cursor to indicate that the program will now respond to Manipulation events.</span></span>
* <span data-ttu-id="65617-313">Уменьшите индекс пальца до бегунка и сохраните их вместе.</span><span class="sxs-lookup"><span data-stu-id="65617-313">Lower your index finger down to your thumb, and keep them pinched together.</span></span>
* <span data-ttu-id="65617-314">Когда вы перемещаете свою руку,-космонавтам тоже перемещается (это манипуляция).</span><span class="sxs-lookup"><span data-stu-id="65617-314">As you move your hand around, the astronaut will move too (this is Manipulation).</span></span>
* <span data-ttu-id="65617-315">Поднимите указатель пальца, чтобы прерывать работу-космонавтам.</span><span class="sxs-lookup"><span data-stu-id="65617-315">Raise your index finger to stop manipulating the astronaut.</span></span>
* <span data-ttu-id="65617-316">Примечание. Если вы не говорите "Move-космонавтам" перед перемещением руки, вместо этого будет использоваться жест навигации.</span><span class="sxs-lookup"><span data-stu-id="65617-316">Note: If you do not say 'Move Astronaut' before moving your hand, then the Navigation gesture will be used instead.</span></span>
* <span data-ttu-id="65617-317">Скажите "повернуть-космонавтам", чтобы вернуться к состоянию ротатабле.</span><span class="sxs-lookup"><span data-stu-id="65617-317">Say 'Rotate Astronaut' to return to the rotatable state.</span></span>

## <a name="chapter-5---model-expansion"></a><span data-ttu-id="65617-318">Глава 5-расширение модели</span><span class="sxs-lookup"><span data-stu-id="65617-318">Chapter 5 - Model expansion</span></span>

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a><span data-ttu-id="65617-319">Задачи</span><span class="sxs-lookup"><span data-stu-id="65617-319">Objectives</span></span>

* <span data-ttu-id="65617-320">Разверните модель-космонавтам на несколько небольших частей, с которыми может взаимодействовать пользователь.</span><span class="sxs-lookup"><span data-stu-id="65617-320">Expand the Astronaut model into multiple, smaller pieces that the user can interact with.</span></span>
* <span data-ttu-id="65617-321">Перемещение каждого элемента по отдельности с помощью жестов навигации и манипуляций.</span><span class="sxs-lookup"><span data-stu-id="65617-321">Move each piece individually using Navigation and Manipulation gestures.</span></span>

### <a name="instructions"></a><span data-ttu-id="65617-322">Инструкции</span><span class="sxs-lookup"><span data-stu-id="65617-322">Instructions</span></span>

<span data-ttu-id="65617-323">В этом разделе мы будем выполнять следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="65617-323">In this section, we will accomplish the following tasks:</span></span>

1. <span data-ttu-id="65617-324">Добавьте новое ключевое слово "**развернуть модель**", чтобы развернуть модель-космонавтам.</span><span class="sxs-lookup"><span data-stu-id="65617-324">Add a new keyword "**Expand Model**" to expand the astronaut model.</span></span>
2. <span data-ttu-id="65617-325">Добавьте новое ключевое слово "**сбросить модель**", чтобы вернуть модель в исходную форму.</span><span class="sxs-lookup"><span data-stu-id="65617-325">Add a new Keyword "**Reset Model**" to return the model to its original form.</span></span>

<span data-ttu-id="65617-326">Это делается путем добавления еще двух ключевых слов в источник речевого ввода из предыдущей главы.</span><span class="sxs-lookup"><span data-stu-id="65617-326">We'll do this by adding two more keywords to the Speech Input Source from the previous chapter.</span></span> <span data-ttu-id="65617-327">Мы также покажем другой способ для работы с событиями распознавания.</span><span class="sxs-lookup"><span data-stu-id="65617-327">We'll also demonstrate another way to handle recognition events.</span></span>

1. <span data-ttu-id="65617-328">Щелкните назад в **астронаутманажер** в **инспекторе** и разверните раздел **Ключевые слова** в **инспекторе**.</span><span class="sxs-lookup"><span data-stu-id="65617-328">Click back on **AstronautManager** in the **Inspector** and expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="65617-329">Щелкните в **+** правой части, чтобы добавить новое ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="65617-329">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="65617-330">Введите ключевое слово как **развернуть модель**.</span><span class="sxs-lookup"><span data-stu-id="65617-330">Type the Keyword as **Expand Model**.</span></span> <span data-ttu-id="65617-331">При необходимости вы можете добавить сочетание клавиш.</span><span class="sxs-lookup"><span data-stu-id="65617-331">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="65617-332">Щелкните в **+** правой части, чтобы добавить новое ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="65617-332">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="65617-333">Введите ключевое слово как **Сброс модели**.</span><span class="sxs-lookup"><span data-stu-id="65617-333">Type the Keyword as **Reset Model**.</span></span> <span data-ttu-id="65617-334">При необходимости вы можете добавить сочетание клавиш.</span><span class="sxs-lookup"><span data-stu-id="65617-334">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="65617-335">На панели **инспектора** нажмите кнопку **Добавить компонент** .</span><span class="sxs-lookup"><span data-stu-id="65617-335">In the **Inspector** panel, click the **Add Component** button.</span></span>
7. <span data-ttu-id="65617-336">В меню введите **обработчик речевого ввода** для поля поиска.</span><span class="sxs-lookup"><span data-stu-id="65617-336">In the menu, type in the search box **Speech Input Handler**.</span></span> <span data-ttu-id="65617-337">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="65617-337">Select the search result.</span></span>
8. <span data-ttu-id="65617-338">Проверьте **глобальный прослушиватель**, так как мы хотим, чтобы эти команды работали независимо от GameObject, на который мы работаем.</span><span class="sxs-lookup"><span data-stu-id="65617-338">Check **Is Global Listener**, since we want these commands to work regardless of the GameObject we're focusing.</span></span>
9. <span data-ttu-id="65617-339">Нажмите кнопку **+** и выберите **развернуть модель** в раскрывающемся списке ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="65617-339">Click the **+** button and select **Expand Model** from the Keyword dropdown.</span></span>
10. <span data-ttu-id="65617-340">Щелкните в **+** разделе ответ и перетащите **Астронаутманажер** из **иерархии** в поле **None (Object) (нет (объект))** .</span><span class="sxs-lookup"><span data-stu-id="65617-340">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
11. <span data-ttu-id="65617-341">Теперь щелкните раскрывающийся список **без функции** , выберите **астронаутманажер**, а затем **експандмоделкомманд**.</span><span class="sxs-lookup"><span data-stu-id="65617-341">Now, click the **No Function** dropdown, select **AstronautManager**, then **ExpandModelCommand**.</span></span>
12. <span data-ttu-id="65617-342">Нажмите кнопку обработчик речевого ввода **+** и выберите **сбросить модель** из раскрывающегося списка ключевых слов.</span><span class="sxs-lookup"><span data-stu-id="65617-342">Click the Speech Input Handler's **+** button and select **Reset Model** from the Keyword dropdown.</span></span>
13. <span data-ttu-id="65617-343">Щелкните в **+** разделе ответ и перетащите **Астронаутманажер** из **иерархии** в поле **None (Object) (нет (объект))** .</span><span class="sxs-lookup"><span data-stu-id="65617-343">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
14. <span data-ttu-id="65617-344">Теперь щелкните раскрывающийся список **без функции** , выберите **астронаутманажер**, а затем **ресетмоделкомманд**.</span><span class="sxs-lookup"><span data-stu-id="65617-344">Now, click the **No Function** dropdown, select **AstronautManager**, then **ResetModelCommand**.</span></span>

![Настройка источника речевого ввода и обработчика для главы 5](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a><span data-ttu-id="65617-346">Построение и Развертывание</span><span class="sxs-lookup"><span data-stu-id="65617-346">Build and Deploy</span></span>

* <span data-ttu-id="65617-347">Тестирование</span><span class="sxs-lookup"><span data-stu-id="65617-347">Try it!</span></span> <span data-ttu-id="65617-348">Выполните сборку и развертывание приложения в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="65617-348">Build and deploy the app to the HoloLens.</span></span>
* <span data-ttu-id="65617-349">Например, **разверните модель** , чтобы увидеть развернутую модель-космонавтам.</span><span class="sxs-lookup"><span data-stu-id="65617-349">Say **Expand Model** to see the expanded astronaut model.</span></span>
* <span data-ttu-id="65617-350">Используйте **навигацию** для вращения отдельных частей-космонавтам масти.</span><span class="sxs-lookup"><span data-stu-id="65617-350">Use **Navigation** to rotate individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="65617-351">Скажем, **переместить-космонавтам** , а затем использовать **манипуляции** для перемещения отдельных частей-космонавтам масти.</span><span class="sxs-lookup"><span data-stu-id="65617-351">Say **Move Astronaut** and then use **Manipulation** to move individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="65617-352">Например, **поверните-космонавтам** , чтобы снова повернуть шашки.</span><span class="sxs-lookup"><span data-stu-id="65617-352">Say **Rotate Astronaut** to rotate the pieces again.</span></span>
* <span data-ttu-id="65617-353">Произнесите **Сброс модели** , чтобы вернуть-космонавтам к исходной форме.</span><span class="sxs-lookup"><span data-stu-id="65617-353">Say **Reset Model** to return the astronaut to its original form.</span></span>

## <a name="the-end"></a><span data-ttu-id="65617-354">Конец</span><span class="sxs-lookup"><span data-stu-id="65617-354">The End</span></span>

<span data-ttu-id="65617-355">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="65617-355">Congratulations!</span></span> <span data-ttu-id="65617-356">Теперь вы выполнили **Ввод MR 211: жест**.</span><span class="sxs-lookup"><span data-stu-id="65617-356">You have now completed **MR Input 211: Gesture**.</span></span>

* <span data-ttu-id="65617-357">Вы узнали, как обнаруживать события отслеживания, навигации и манипуляции, а также реагировать на них.</span><span class="sxs-lookup"><span data-stu-id="65617-357">You know how to detect and respond to hand tracking, navigation and manipulation events.</span></span>
* <span data-ttu-id="65617-358">Вы понимаете разницу между жестами навигации и манипуляциями.</span><span class="sxs-lookup"><span data-stu-id="65617-358">You understand the difference between Navigation and Manipulation gestures.</span></span>
* <span data-ttu-id="65617-359">Вы узнаете, как изменить курсор, чтобы обеспечить визуальную обратную связь при обнаружении руки, когда рука собирается потеряться и когда объект поддерживает различные взаимодействия (Навигация и манипуляция).</span><span class="sxs-lookup"><span data-stu-id="65617-359">You know how to change the cursor to provide visual feedback for when a hand is detected, when a hand is about to be lost, and for when an object supports different interactions (Navigation vs Manipulation).</span></span>