---
title: 211. Ввод в смешанной реальности — жест
description: Выполните приведенное ниже пошаговое руководство по программированию с помощью Unity, Visual Studio и HoloLens, чтобы узнать о концепциях жестов.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: холотулкит, микседреалититулкит, микседреалититулкит-Unity, Academy, руководство, жест, HoloLens, Mixed Reality, Unity, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, Windows 10
ms.openlocfilehash: 9f83e2f3b02cf8d83b2fb58a3a0d05dc8576b0e8
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678293"
---
# <a name="mr-input-211-gesture"></a><span data-ttu-id="83c66-104">211. Ввод в смешанной реальности: жесты</span><span class="sxs-lookup"><span data-stu-id="83c66-104">MR Input 211: Gesture</span></span>

>[!NOTE]
><span data-ttu-id="83c66-105">Руководства Mixed Reality Academy были разработаны для иммерсивных гарнитур HoloLens (1-го поколения) и иммерсивных гарнитур Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="83c66-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="83c66-106">Поэтому мы считаем, что важно оставить эти руководства для разработчиков, которые ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="83c66-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="83c66-107">Данные руководства **_не_** будут обновляться с учетом последних наборов инструментов или возможностей взаимодействия для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="83c66-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="83c66-108">Они будут сохранены для работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="83c66-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="83c66-109">Опубликован [новый цикл руководств](../../../mr-learning-base-01.md) для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="83c66-109">[A new series of tutorials](../../../mr-learning-base-01.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="83c66-110">[Жесты](../../../design/gaze-and-commit.md#composite-gestures) применяют намерение пользователя к действию.</span><span class="sxs-lookup"><span data-stu-id="83c66-110">[Gestures](../../../design/gaze-and-commit.md#composite-gestures) turn user intention into action.</span></span> <span data-ttu-id="83c66-111">С помощью жестов пользователи могут взаимодействовать с голограммами.</span><span class="sxs-lookup"><span data-stu-id="83c66-111">With gestures, users can interact with holograms.</span></span> <span data-ttu-id="83c66-112">В этом курсе мы расскажем, как контролировать руки пользователя, реагировать на вводимые пользователем данные и предоставлять отзыв пользователю в зависимости от состояния и местоположения.</span><span class="sxs-lookup"><span data-stu-id="83c66-112">In this course, we'll learn how to track the user's hands, respond to user input, and give feedback to the user based on hand state and location.</span></span>

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

<span data-ttu-id="83c66-113">В статье об [основных принципах MR 101](../../../develop/unity/tutorials/holograms-101.md)мы использовали простой жест касания для взаимодействия с нашими голограммами.</span><span class="sxs-lookup"><span data-stu-id="83c66-113">In [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md), we used a simple air-tap gesture to interact with our holograms.</span></span> <span data-ttu-id="83c66-114">Теперь мы перейдем к жесту в области воздушного касания и изучим новые концепции:</span><span class="sxs-lookup"><span data-stu-id="83c66-114">Now, we'll move beyond the air-tap gesture and explore new concepts to:</span></span>

* <span data-ttu-id="83c66-115">Обнаружение времени трассировки пользователя и предоставление отзыва пользователю.</span><span class="sxs-lookup"><span data-stu-id="83c66-115">Detect when the user's hand is being tracked and provide feedback to the user.</span></span>
* <span data-ttu-id="83c66-116">Используйте жест навигации для поворота голограмм.</span><span class="sxs-lookup"><span data-stu-id="83c66-116">Use a navigation gesture to rotate our holograms.</span></span>
* <span data-ttu-id="83c66-117">Предоставьте отзыв о том, когда пользователь перейдет из режима руки.</span><span class="sxs-lookup"><span data-stu-id="83c66-117">Provide feedback when the user's hand is about to go out of view.</span></span>
* <span data-ttu-id="83c66-118">Используйте события манипуляции, чтобы позволить пользователям перемещать голограммы с помощью их руки.</span><span class="sxs-lookup"><span data-stu-id="83c66-118">Use manipulation events to allow users to move holograms with their hands.</span></span>

<span data-ttu-id="83c66-119">В этом курсе мы будем посещать **Обозреватель моделей** проектов Unity, который мы создали в [MR input 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="83c66-119">In this course, we'll revisit the Unity project **Model Explorer**, which we built in [MR Input 210](holograms-210.md).</span></span> <span data-ttu-id="83c66-120">Наш-космонавтамный дружественный подход назад поможет нам в исследовании новых концепций жестов.</span><span class="sxs-lookup"><span data-stu-id="83c66-120">Our astronaut friend is back to assist us in our exploration of these new gesture concepts.</span></span>

>[!IMPORTANT]
><span data-ttu-id="83c66-121">Видеоматериалы, внедренные в каждую из приведенных ниже глав, были записаны с использованием более старой версии Unity и набора средств Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="83c66-121">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="83c66-122">Хотя пошаговые инструкции являются точными и актуальными, в соответствующих видеоматериалах могут отображаться сценарии и визуальные элементы, которые являются неактуальными.</span><span class="sxs-lookup"><span data-stu-id="83c66-122">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="83c66-123">Видеоматериалы по-прежнему включены в постерити, так как эти концепции все еще применимы.</span><span class="sxs-lookup"><span data-stu-id="83c66-123">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="83c66-124">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="83c66-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="83c66-125">Курс</span><span class="sxs-lookup"><span data-stu-id="83c66-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="83c66-126"><a href="../../../hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="83c66-126"><a href="../../../hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="83c66-127"><a href="../../../discover/immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="83c66-127"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="83c66-128">211. Ввод в смешанной реальности: жесты</span><span class="sxs-lookup"><span data-stu-id="83c66-128">MR Input 211: Gesture</span></span></td><td style="text-align: center;"> <span data-ttu-id="83c66-129">✔️</span><span class="sxs-lookup"><span data-stu-id="83c66-129">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="83c66-130">✔️</span><span class="sxs-lookup"><span data-stu-id="83c66-130">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="83c66-131">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="83c66-131">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="83c66-132">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="83c66-132">Prerequisites</span></span>

* <span data-ttu-id="83c66-133">КОМПЬЮТЕР с Windows 10, на котором [установлены правильные средства](../../../develop/install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="83c66-133">A Windows 10 PC configured with the correct [tools installed](../../../develop/install-the-tools.md).</span></span>
* <span data-ttu-id="83c66-134">Некоторые основные возможности программирования на C#.</span><span class="sxs-lookup"><span data-stu-id="83c66-134">Some basic C# programming ability.</span></span>
* <span data-ttu-id="83c66-135">Вы должны были выполнить [Основные сведения о MR 101](../../../develop/unity/tutorials/holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="83c66-135">You should have completed [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md).</span></span>
* <span data-ttu-id="83c66-136">Необходимо завершить [Ввод MR 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="83c66-136">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="83c66-137">Устройство HoloLens, [настроенное для разработки](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="83c66-137">A HoloLens device [configured for development](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="83c66-138">Файлы проекта</span><span class="sxs-lookup"><span data-stu-id="83c66-138">Project files</span></span>

* <span data-ttu-id="83c66-139">Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) , необходимые для проекта.</span><span class="sxs-lookup"><span data-stu-id="83c66-139">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) required by the project.</span></span> <span data-ttu-id="83c66-140">Требуется Unity 2017,2 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="83c66-140">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="83c66-141">Отмена архивации файлов на Рабочий стол или другого места для удобства доступа.</span><span class="sxs-lookup"><span data-stu-id="83c66-141">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="83c66-142">Если вы хотите просмотреть исходный код перед загрузкой, он [доступен на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span><span class="sxs-lookup"><span data-stu-id="83c66-142">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="83c66-143">Ошибки и примечания</span><span class="sxs-lookup"><span data-stu-id="83c66-143">Errata and Notes</span></span>

* <span data-ttu-id="83c66-144">Параметр "Enable Только мой код" должен быть отключен (*снят*) в Visual Studio в разделе "сервис->параметры" — >Отладка для попадания в код точек останова в коде.</span><span class="sxs-lookup"><span data-stu-id="83c66-144">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-0---unity-setup"></a><span data-ttu-id="83c66-145">Глава 0-Установка Unity</span><span class="sxs-lookup"><span data-stu-id="83c66-145">Chapter 0 - Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="83c66-146">Инструкции</span><span class="sxs-lookup"><span data-stu-id="83c66-146">Instructions</span></span>

1. <span data-ttu-id="83c66-147">Запустите Unity.</span><span class="sxs-lookup"><span data-stu-id="83c66-147">Start Unity.</span></span>
2. <span data-ttu-id="83c66-148">Щелкните **Open**(Открыть).</span><span class="sxs-lookup"><span data-stu-id="83c66-148">Select **Open**.</span></span>
3. <span data-ttu-id="83c66-149">Перейдите к папке **жестов** , для которой был отменен Архив.</span><span class="sxs-lookup"><span data-stu-id="83c66-149">Navigate to the **Gesture** folder you previously un-archived.</span></span>
4. <span data-ttu-id="83c66-150">Найдите и выберите **начальную** / папку **обозревателя моделей** .</span><span class="sxs-lookup"><span data-stu-id="83c66-150">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="83c66-151">Нажмите кнопку **выбрать папку** .</span><span class="sxs-lookup"><span data-stu-id="83c66-151">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="83c66-152">На панели **проект** разверните папку **сцены** .</span><span class="sxs-lookup"><span data-stu-id="83c66-152">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="83c66-153">Дважды щелкните **моделексплорер** сцену, чтобы загрузить его в Unity.</span><span class="sxs-lookup"><span data-stu-id="83c66-153">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="83c66-154">Сборка</span><span class="sxs-lookup"><span data-stu-id="83c66-154">Building</span></span>

1. <span data-ttu-id="83c66-155">В Unity выберите **файл > параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="83c66-155">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="83c66-156">Если « **сцены» или «моделексплорер** » в окне « **Построение**» не отображаются, щелкните **Добавить открытые сцены** , чтобы добавить сцену.</span><span class="sxs-lookup"><span data-stu-id="83c66-156">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="83c66-157">Если вы специально разрабатываете для HoloLens, задайте для параметра **целевое устройство** значение **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="83c66-157">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="83c66-158">В противном случае оставьте его на **любом устройстве**.</span><span class="sxs-lookup"><span data-stu-id="83c66-158">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="83c66-159">Убедитесь, что для **типа сборки** задано значение **D3D** и **пакет SDK** установлен в значение " **Последняя установленная версия** " (это должен быть пакет SDK 16299 или более поздней версии).</span><span class="sxs-lookup"><span data-stu-id="83c66-159">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="83c66-160">Щелкните **Построить**.</span><span class="sxs-lookup"><span data-stu-id="83c66-160">Click **Build**.</span></span>
6. <span data-ttu-id="83c66-161">Создайте **новую папку** с именем App.</span><span class="sxs-lookup"><span data-stu-id="83c66-161">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="83c66-162">Щелкните папку **приложения** одним щелчком мыши.</span><span class="sxs-lookup"><span data-stu-id="83c66-162">Single click the **App** folder.</span></span>
8. <span data-ttu-id="83c66-163">Нажмите кнопку **выбрать папку** , и Unity начнет создавать проект для Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="83c66-163">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="83c66-164">После завершения Unity появится окно проводника.</span><span class="sxs-lookup"><span data-stu-id="83c66-164">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="83c66-165">Откройте папку **приложения** .</span><span class="sxs-lookup"><span data-stu-id="83c66-165">Open the **App** folder.</span></span>
2. <span data-ttu-id="83c66-166">Откройте **решение Моделексплорер Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="83c66-166">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="83c66-167">При развертывании в HoloLens:</span><span class="sxs-lookup"><span data-stu-id="83c66-167">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="83c66-168">С помощью верхней панели инструментов в Visual Studio измените целевой объект с отладка на **выпуск** и с ARM на **x86**.</span><span class="sxs-lookup"><span data-stu-id="83c66-168">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="83c66-169">Щелкните стрелку раскрывающегося списка рядом с кнопкой локальный компьютер и выберите **Удаленный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="83c66-169">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="83c66-170">Введите **IP-адрес устройства HoloLens** и задайте для режима проверки подлинности значение **универсальный (незашифрованный протокол)**.</span><span class="sxs-lookup"><span data-stu-id="83c66-170">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="83c66-171">Нажмите кнопку **Выбрать**.</span><span class="sxs-lookup"><span data-stu-id="83c66-171">Click **Select**.</span></span> <span data-ttu-id="83c66-172">Если вы не узнаете IP-адрес устройства, проверьте **параметры > сеть & интернет > дополнительные параметры**.</span><span class="sxs-lookup"><span data-stu-id="83c66-172">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="83c66-173">В верхней строке меню щелкните **Отладка-> начать без отладки** или нажмите клавиши **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="83c66-173">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="83c66-174">Если вы впервые развертываете на устройстве, вам потребуется [связать его с Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).</span><span class="sxs-lookup"><span data-stu-id="83c66-174">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).</span></span>
5. <span data-ttu-id="83c66-175">После развертывания приложения закройте **фитбокс** с помощью **жеста выбора**.</span><span class="sxs-lookup"><span data-stu-id="83c66-175">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="83c66-176">При развертывании на иммерсивное головной телефон:</span><span class="sxs-lookup"><span data-stu-id="83c66-176">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="83c66-177">С помощью верхней панели инструментов в Visual Studio измените целевой объект с отладка на **выпуск** и с ARM на **x64**.</span><span class="sxs-lookup"><span data-stu-id="83c66-177">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="83c66-178">Убедитесь, что для целевого объекта развертывания задано значение **локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="83c66-178">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="83c66-179">В верхней строке меню щелкните **Отладка-> начать без отладки** или нажмите клавиши **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="83c66-179">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="83c66-180">После развертывания приложения закройте **фитбокс** , изменив триггер на контроллере движения.</span><span class="sxs-lookup"><span data-stu-id="83c66-180">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="83c66-181">Вы можете заметить некоторые красные ошибки на панели ошибок Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="83c66-181">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="83c66-182">Их можно спокойно игнорировать.</span><span class="sxs-lookup"><span data-stu-id="83c66-182">It is safe to ignore them.</span></span> <span data-ttu-id="83c66-183">Переключитесь на панель вывода для просмотра фактического хода построения.</span><span class="sxs-lookup"><span data-stu-id="83c66-183">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="83c66-184">Ошибки на панели вывода потребует внесения исправления (чаще всего они вызваны ошибкой в скрипте).</span><span class="sxs-lookup"><span data-stu-id="83c66-184">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---hand-detected-feedback"></a><span data-ttu-id="83c66-185">Глава 1. обнаружена обратная связь</span><span class="sxs-lookup"><span data-stu-id="83c66-185">Chapter 1 - Hand detected feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a><span data-ttu-id="83c66-186">Цели</span><span class="sxs-lookup"><span data-stu-id="83c66-186">Objectives</span></span>

* <span data-ttu-id="83c66-187">Подпишитесь на события отслеживания.</span><span class="sxs-lookup"><span data-stu-id="83c66-187">Subscribe to hand tracking events.</span></span>
* <span data-ttu-id="83c66-188">Используйте обратную связь курсора для отображения пользователей при отслеживании руки.</span><span class="sxs-lookup"><span data-stu-id="83c66-188">Use cursor feedback to show users when a hand is being tracked.</span></span>

>[!NOTE]
><span data-ttu-id="83c66-189">В HoloLens 2 обнаруженные руки срабатывают каждый раз, когда видны руки (а не только при наведении указателя мыши на палец).</span><span class="sxs-lookup"><span data-stu-id="83c66-189">On HoloLens 2 , hands detected fires whenever hands are visible (not just when a finger is pointing up).</span></span>

### <a name="instructions"></a><span data-ttu-id="83c66-190">Инструкции</span><span class="sxs-lookup"><span data-stu-id="83c66-190">Instructions</span></span>

* <span data-ttu-id="83c66-191">На панели **Иерархия** разверните объект **InputManager** .</span><span class="sxs-lookup"><span data-stu-id="83c66-191">In the **Hierarchy** panel, expand the **InputManager** object.</span></span>
* <span data-ttu-id="83c66-192">Найдите и выберите объект **жестуресинпут** .</span><span class="sxs-lookup"><span data-stu-id="83c66-192">Look for and select the **GesturesInput** object.</span></span>

<span data-ttu-id="83c66-193">Сценарий **InteractionInputSource.CS** выполняет следующие действия:</span><span class="sxs-lookup"><span data-stu-id="83c66-193">The **InteractionInputSource.cs** script performs these steps:</span></span>

1. <span data-ttu-id="83c66-194">Подписывается на события Интерактионсаурцедетектед и Интерактионсаурцелост.</span><span class="sxs-lookup"><span data-stu-id="83c66-194">Subscribes to the InteractionSourceDetected and InteractionSourceLost events.</span></span>
2. <span data-ttu-id="83c66-195">Задает состояние Ханддетектед.</span><span class="sxs-lookup"><span data-stu-id="83c66-195">Sets the HandDetected state.</span></span>
3. <span data-ttu-id="83c66-196">Отменяет подписывание событий Интерактионсаурцедетектед и Интерактионсаурцелост.</span><span class="sxs-lookup"><span data-stu-id="83c66-196">Unsubscribes from the InteractionSourceDetected and InteractionSourceLost events.</span></span>

<span data-ttu-id="83c66-197">Далее мы будем обновлять наш курсор с [MR Input 210](holograms-210.md) на тот, который отображает отзыв в зависимости от действий пользователя.</span><span class="sxs-lookup"><span data-stu-id="83c66-197">Next, we'll upgrade our cursor from [MR Input 210](holograms-210.md) into one that shows feedback depending on the user's actions.</span></span>

1. <span data-ttu-id="83c66-198">На панели **Иерархия** выберите объект **курсора** и удалите его.</span><span class="sxs-lookup"><span data-stu-id="83c66-198">In the **Hierarchy** panel, select the **Cursor** object and delete it.</span></span>
2. <span data-ttu-id="83c66-199">На панели **проект** найдите **курсорвисфидбакк** и перетащите его на панель **Иерархия** .</span><span class="sxs-lookup"><span data-stu-id="83c66-199">In the **Project** panel, search for **CursorWithFeedback** and drag it into the **Hierarchy** panel.</span></span>
3. <span data-ttu-id="83c66-200">Щелкните **InputManager** на панели **Иерархия** , а затем перетащите объект **Курсорвисфидбакк** из **иерархии** в поле **курсора** InputManager **симплесинглепоинтерселектор** в нижней части **инспектора**.</span><span class="sxs-lookup"><span data-stu-id="83c66-200">Click on **InputManager** in the **Hierarchy** panel, then drag the **CursorWithFeedback** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>
4. <span data-ttu-id="83c66-201">Щелкните **курсорвисфидбакк** в **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="83c66-201">Click on the **CursorWithFeedback** in the **Hierarchy**.</span></span>
5. <span data-ttu-id="83c66-202">На панели **инспектора** раскройте **данные о состоянии курсора** в скрипте **объект курсора** .</span><span class="sxs-lookup"><span data-stu-id="83c66-202">In the **Inspector** panel, expand **Cursor State Data** on the **Object Cursor** script.</span></span>

<span data-ttu-id="83c66-203">**Данные о состоянии курсора** работают следующим образом:</span><span class="sxs-lookup"><span data-stu-id="83c66-203">The **Cursor State Data** works like this:</span></span>

* <span data-ttu-id="83c66-204">Любое состояние **наблюдения** означает, что не обнаружена рука, и пользователь просто смотрит на экран.</span><span class="sxs-lookup"><span data-stu-id="83c66-204">Any **Observe** state means that no hand is detected and the user is simply looking around.</span></span>
* <span data-ttu-id="83c66-205">Любое состояние **взаимодействия** означает, что обнаружена рука или контроллер.</span><span class="sxs-lookup"><span data-stu-id="83c66-205">Any **Interact** state means that a hand or controller is detected.</span></span>
* <span data-ttu-id="83c66-206">Любое состояние **наведения указателя** означает, что пользователь смотрит на голограмму.</span><span class="sxs-lookup"><span data-stu-id="83c66-206">Any **Hover** state means the user is looking at a hologram.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="83c66-207">Построение и Развертывание</span><span class="sxs-lookup"><span data-stu-id="83c66-207">Build and Deploy</span></span>

* <span data-ttu-id="83c66-208">В Unity используйте **параметры сборки File >** для перестроения приложения.</span><span class="sxs-lookup"><span data-stu-id="83c66-208">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="83c66-209">Откройте папку **приложения** .</span><span class="sxs-lookup"><span data-stu-id="83c66-209">Open the **App** folder.</span></span>
* <span data-ttu-id="83c66-210">Откройте **решение Моделексплорер Visual Studio**, если оно еще не открыто.</span><span class="sxs-lookup"><span data-stu-id="83c66-210">If it's not already open, open the **ModelExplorer Visual Studio Solution**.</span></span>
  * <span data-ttu-id="83c66-211">(Если вы уже создали и развернули этот проект в Visual Studio во время настройки, то можете открыть этот экземпляр VS и нажать кнопку "перезагрузить все" при появлении соответствующего запроса).</span><span class="sxs-lookup"><span data-stu-id="83c66-211">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>
* <span data-ttu-id="83c66-212">В Visual Studio щелкните **Отладка-> начать без отладки** или нажмите клавиши **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="83c66-212">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="83c66-213">После развертывания приложения в HoloLens закройте фитбокс с помощью жеста касания.</span><span class="sxs-lookup"><span data-stu-id="83c66-213">After the application deploys to the HoloLens, dismiss the fitbox using the air-tap gesture.</span></span>
* <span data-ttu-id="83c66-214">Переместите руку в режим просмотра и наведите указатель пальца на положение "небесно", чтобы начать отслеживание.</span><span class="sxs-lookup"><span data-stu-id="83c66-214">Move your hand into view and point your index finger to the sky to start hand tracking.</span></span>
* <span data-ttu-id="83c66-215">Переместите руку влево, вправо, вверх и вниз.</span><span class="sxs-lookup"><span data-stu-id="83c66-215">Move your hand left, right, up and down.</span></span>
* <span data-ttu-id="83c66-216">Посмотрите, как меняется вид курсора при обнаружении и утере руки.</span><span class="sxs-lookup"><span data-stu-id="83c66-216">Watch how the cursor changes when your hand is detected and then lost from view.</span></span>
* <span data-ttu-id="83c66-217">Если вы используете иммерсивное головной телефон, вам потребуется подключиться к контроллеру и отключить его.</span><span class="sxs-lookup"><span data-stu-id="83c66-217">If you're on an immersive headset, you'll have to connect and disconnect your controller.</span></span> <span data-ttu-id="83c66-218">Этот отзыв становится менее интересным на иммерсивное устройство, так как подключенный контроллер всегда будет "доступен".</span><span class="sxs-lookup"><span data-stu-id="83c66-218">This feedback becomes less interesting on an immersive device, as a connected controller will always be "available".</span></span>

## <a name="chapter-2---navigation"></a><span data-ttu-id="83c66-219">Глава 2. Навигация</span><span class="sxs-lookup"><span data-stu-id="83c66-219">Chapter 2 - Navigation</span></span>

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a><span data-ttu-id="83c66-220">Цели</span><span class="sxs-lookup"><span data-stu-id="83c66-220">Objectives</span></span>

* <span data-ttu-id="83c66-221">Используйте события жестов навигации для вращения-космонавтам.</span><span class="sxs-lookup"><span data-stu-id="83c66-221">Use Navigation gesture events to rotate the astronaut.</span></span>

### <a name="instructions"></a><span data-ttu-id="83c66-222">Инструкции</span><span class="sxs-lookup"><span data-stu-id="83c66-222">Instructions</span></span>

<span data-ttu-id="83c66-223">Чтобы использовать жесты навигации в нашем приложении, мы собираемся изменить **GestureAction.CS** для поворота объектов при появлении жеста навигации.</span><span class="sxs-lookup"><span data-stu-id="83c66-223">To use Navigation gestures in our app, we are going to edit **GestureAction.cs** to rotate objects when the Navigation gesture occurs.</span></span> <span data-ttu-id="83c66-224">Кроме того, мы добавим отзыв к курсору, который будет отображаться, когда доступна Навигация.</span><span class="sxs-lookup"><span data-stu-id="83c66-224">Additionally, we'll add feedback to the cursor to display when Navigation is available.</span></span>

1. <span data-ttu-id="83c66-225">На панели **Иерархия** разверните узел **курсорвисфидбакк**.</span><span class="sxs-lookup"><span data-stu-id="83c66-225">In the **Hierarchy** panel, expand **CursorWithFeedback**.</span></span>
2. <span data-ttu-id="83c66-226">В папке **голограмм** найдите ресурс **скроллфидбакк** .</span><span class="sxs-lookup"><span data-stu-id="83c66-226">In the **Holograms** folder, find the **ScrollFeedback** asset.</span></span>
3. <span data-ttu-id="83c66-227">Перетащите **скроллфидбакк** prefab на **Курсорвисфидбакк** GameObject в **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="83c66-227">Drag and drop the **ScrollFeedback** prefab onto the **CursorWithFeedback** GameObject in the **Hierarchy**.</span></span>
4. <span data-ttu-id="83c66-228">Щелкните **курсорвисфидбакк**.</span><span class="sxs-lookup"><span data-stu-id="83c66-228">Click on **CursorWithFeedback**.</span></span>
5. <span data-ttu-id="83c66-229">На панели **инспектора** нажмите кнопку **Добавить компонент** .</span><span class="sxs-lookup"><span data-stu-id="83c66-229">In the **Inspector** panel, click the **Add Component** button.</span></span>
6. <span data-ttu-id="83c66-230">В меню введите **курсорфидбакк** в поле поиска.</span><span class="sxs-lookup"><span data-stu-id="83c66-230">In the menu, type in the search box **CursorFeedback**.</span></span> <span data-ttu-id="83c66-231">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="83c66-231">Select the search result.</span></span>
7. <span data-ttu-id="83c66-232">Перетащите объект **скроллфидбакк** из **иерархии** в свойство игровое поле, **обнаруженное прокруткой** в окне " **отзыв курсора** " в **инспекторе**.</span><span class="sxs-lookup"><span data-stu-id="83c66-232">Drag and drop the **ScrollFeedback** object from the **Hierarchy** onto the **Scroll Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>
8. <span data-ttu-id="83c66-233">На панели **Иерархия** выберите объект **астроман** .</span><span class="sxs-lookup"><span data-stu-id="83c66-233">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
9. <span data-ttu-id="83c66-234">На панели **инспектора** нажмите кнопку **Добавить компонент** .</span><span class="sxs-lookup"><span data-stu-id="83c66-234">In the **Inspector** panel, click the **Add Component** button.</span></span>
10. <span data-ttu-id="83c66-235">В меню введите **действие жеста** поля поиска.</span><span class="sxs-lookup"><span data-stu-id="83c66-235">In the menu, type in the search box **Gesture Action**.</span></span> <span data-ttu-id="83c66-236">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="83c66-236">Select the search result.</span></span>

<span data-ttu-id="83c66-237">Затем откройте **GestureAction.CS** в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="83c66-237">Next, open **GestureAction.cs** in Visual Studio.</span></span> <span data-ttu-id="83c66-238">В написании упражнения 2. c измените сценарий, чтобы сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="83c66-238">In coding exercise 2.c, edit the script to do the following:</span></span>

1. <span data-ttu-id="83c66-239">**Поворот объекта астроман** при выполнении жеста навигации.</span><span class="sxs-lookup"><span data-stu-id="83c66-239">**Rotate the AstroMan** object whenever a Navigation gesture is performed.</span></span>
2. <span data-ttu-id="83c66-240">Вычислите **ротатионфактор** , чтобы управлять объемом вращения, применяемого к объекту.</span><span class="sxs-lookup"><span data-stu-id="83c66-240">Calculate the **rotationFactor** to control the amount of rotation applied to the object.</span></span>
3. <span data-ttu-id="83c66-241">**Поворот объекта** вокруг оси y, когда пользователь перемещает руку влево или вправо.</span><span class="sxs-lookup"><span data-stu-id="83c66-241">**Rotate the object** around the y-axis when the user moves their hand left or right.</span></span>

<span data-ttu-id="83c66-242">Выполните кодирование упражнений 2. c в скрипте или замените код завершенным решением ниже:</span><span class="sxs-lookup"><span data-stu-id="83c66-242">Complete coding exercises 2.c in the script, or replace the code with the completed solution below:</span></span>

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

<span data-ttu-id="83c66-243">Вы заметите, что другие события навигации уже заполнены некоторыми сведениями.</span><span class="sxs-lookup"><span data-stu-id="83c66-243">You'll notice that the other navigation events are already filled in with some info.</span></span> <span data-ttu-id="83c66-244">Мы принудительно GameObject в модальный стек Инпутсистем'с в наборе, поэтому пользователю не нужно поддерживать фокус на-космонавтам после начала вращения.</span><span class="sxs-lookup"><span data-stu-id="83c66-244">We push the GameObject onto the Toolkit's InputSystem's modal stack, so the user doesn't have to maintain focus on the Astronaut once rotation has begun.</span></span> <span data-ttu-id="83c66-245">Соответственно, при завершении жеста GameObjectся из стека.</span><span class="sxs-lookup"><span data-stu-id="83c66-245">Correspondingly, we pop the GameObject off the stack once the gesture is completed.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="83c66-246">Построение и Развертывание</span><span class="sxs-lookup"><span data-stu-id="83c66-246">Build and Deploy</span></span>

1. <span data-ttu-id="83c66-247">Перестройте приложение в Unity, а затем выполните сборку и развертывание из Visual Studio, чтобы запустить его в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="83c66-247">Rebuild the application in Unity and then build and deploy from Visual Studio to run it in the HoloLens.</span></span>
2. <span data-ttu-id="83c66-248">Взгляните на-космонавтам, на обеих сторонах курсора должны появиться две стрелки.</span><span class="sxs-lookup"><span data-stu-id="83c66-248">Gaze at the astronaut, two arrows should appear on either side of the cursor.</span></span> <span data-ttu-id="83c66-249">Этот новый визуальный элемент означает, что-космонавтам можно поворачивать.</span><span class="sxs-lookup"><span data-stu-id="83c66-249">This new visual indicates that the astronaut can be rotated.</span></span>
3. <span data-ttu-id="83c66-250">Поместите руку в готовую позицию (указатель пальца, указывающий на перевозки), чтобы HoloLens начал отслеживать свою руку.</span><span class="sxs-lookup"><span data-stu-id="83c66-250">Place your hand in the ready position (index finger pointed towards the sky) so the HoloLens will start tracking your hand.</span></span>
4. <span data-ttu-id="83c66-251">Чтобы повернуть-космонавтам, уменьшите индекс пальца до позиции сжатия, а затем переместите руку влево или вправо, чтобы активировать жест Навигатионкс.</span><span class="sxs-lookup"><span data-stu-id="83c66-251">To rotate the astronaut, lower your index finger to a pinch position, and then move your hand left or right to trigger the NavigationX gesture.</span></span>

## <a name="chapter-3---hand-guidance"></a><span data-ttu-id="83c66-252">Глава 3. Руководство по использованию</span><span class="sxs-lookup"><span data-stu-id="83c66-252">Chapter 3 - Hand Guidance</span></span>

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a><span data-ttu-id="83c66-253">Цели</span><span class="sxs-lookup"><span data-stu-id="83c66-253">Objectives</span></span>

* <span data-ttu-id="83c66-254">Используйте **оценку руководства** для прогнозирования того, что отслеживание будет потеряно.</span><span class="sxs-lookup"><span data-stu-id="83c66-254">Use **hand guidance score** to help predict when hand tracking will be lost.</span></span>
* <span data-ttu-id="83c66-255">Оставить **отзыв о курсоре** , чтобы показать, когда рука пользователя приближается к границе представления.</span><span class="sxs-lookup"><span data-stu-id="83c66-255">Provide **feedback on the cursor** to show when the user's hand nears the camera's edge of view.</span></span>

### <a name="instructions"></a><span data-ttu-id="83c66-256">Инструкции</span><span class="sxs-lookup"><span data-stu-id="83c66-256">Instructions</span></span>

1. <span data-ttu-id="83c66-257">На панели **Иерархия** выберите объект **курсорвисфидбакк** .</span><span class="sxs-lookup"><span data-stu-id="83c66-257">In the **Hierarchy** panel, select the **CursorWithFeedback** object.</span></span>
2. <span data-ttu-id="83c66-258">На панели **инспектора** нажмите кнопку **Добавить компонент** .</span><span class="sxs-lookup"><span data-stu-id="83c66-258">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="83c66-259">В меню введите в поле **поиска.**</span><span class="sxs-lookup"><span data-stu-id="83c66-259">In the menu, type in the search box **Hand Guidance**.</span></span> <span data-ttu-id="83c66-260">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="83c66-260">Select the search result.</span></span>
4. <span data-ttu-id="83c66-261">В папке **голограммы** на панели **проекта** найдите ресурс **хандгуиданцефидбакк** .</span><span class="sxs-lookup"><span data-stu-id="83c66-261">In the **Project** panel **Holograms** folder, find the **HandGuidanceFeedback** asset.</span></span>
5. <span data-ttu-id="83c66-262">Перетащите ресурс **хандгуиданцефидбакк** в свойство **индикатор "рука** " на панели **инспектора** .</span><span class="sxs-lookup"><span data-stu-id="83c66-262">Drag and drop the **HandGuidanceFeedback** asset onto the **Hand Guidance Indicator** property in the **Inspector** panel.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="83c66-263">Построение и Развертывание</span><span class="sxs-lookup"><span data-stu-id="83c66-263">Build and Deploy</span></span>

* <span data-ttu-id="83c66-264">Перестройте приложение в Unity, а затем выполните сборку и развертывание из Visual Studio для работы с приложением в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="83c66-264">Rebuild the application in Unity and then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="83c66-265">Перенесите руку, чтобы просмотреть и подать указатель на палец.</span><span class="sxs-lookup"><span data-stu-id="83c66-265">Bring your hand into view and raise your index finger to get tracked.</span></span>
* <span data-ttu-id="83c66-266">Начните вращение-космонавтам с помощью жеста навигации (сжатие индекса и палец вместе).</span><span class="sxs-lookup"><span data-stu-id="83c66-266">Start rotating the astronaut with the Navigation gesture (pinch your index finger and thumb together).</span></span>
* <span data-ttu-id="83c66-267">Переместите руку налево, вправо, вверх и вниз.</span><span class="sxs-lookup"><span data-stu-id="83c66-267">Move your hand far left, right, up, and down.</span></span>
* <span data-ttu-id="83c66-268">По мере того, как приближается граница рамки жеста, рядом с курсором должна появиться стрелка, чтобы предупредить, что отслеживание будет потеряно.</span><span class="sxs-lookup"><span data-stu-id="83c66-268">As your hand nears the edge of the gesture frame, an arrow should appear next to the cursor to warn you that hand tracking will be lost.</span></span> <span data-ttu-id="83c66-269">Стрелка указывает направление движения руки, чтобы предотвратить потерю отслеживания.</span><span class="sxs-lookup"><span data-stu-id="83c66-269">The arrow indicates which direction to move your hand in order to prevent tracking from being lost.</span></span>

## <a name="chapter-4---manipulation"></a><span data-ttu-id="83c66-270">Глава 4. Управление</span><span class="sxs-lookup"><span data-stu-id="83c66-270">Chapter 4 - Manipulation</span></span>

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a><span data-ttu-id="83c66-271">Цели</span><span class="sxs-lookup"><span data-stu-id="83c66-271">Objectives</span></span>

* <span data-ttu-id="83c66-272">Используйте события манипуляции для перемещения-космонавтам с помощью стрелок.</span><span class="sxs-lookup"><span data-stu-id="83c66-272">Use Manipulation events to move the astronaut with your hands.</span></span>
* <span data-ttu-id="83c66-273">Предоставьте отзыв о курсоре, чтобы пользователь мог понять, когда можно использовать манипуляцию.</span><span class="sxs-lookup"><span data-stu-id="83c66-273">Provide feedback on the cursor to let the user know when Manipulation can be used.</span></span>

### <a name="instructions"></a><span data-ttu-id="83c66-274">Инструкции</span><span class="sxs-lookup"><span data-stu-id="83c66-274">Instructions</span></span>

<span data-ttu-id="83c66-275">GestureManager.cs и AstronautManager.cs позволят нам выполнить следующие действия:</span><span class="sxs-lookup"><span data-stu-id="83c66-275">GestureManager.cs and AstronautManager.cs will allow us to do the following:</span></span>

1. <span data-ttu-id="83c66-276">Используйте ключевое слово "**Move-космонавтам**" для распознавания речи, чтобы включить жесты **манипуляции** и "**повернуть-космонавтам**", чтобы отключить их.</span><span class="sxs-lookup"><span data-stu-id="83c66-276">Use the speech keyword "**Move Astronaut**" to enable **Manipulation** gestures and "**Rotate Astronaut**" to disable them.</span></span>
2. <span data-ttu-id="83c66-277">Переключитесь на реакцию **распознавателя жестов манипуляции**.</span><span class="sxs-lookup"><span data-stu-id="83c66-277">Switch to responding to the **Manipulation Gesture Recognizer**.</span></span>

<span data-ttu-id="83c66-278">Давайте начнем.</span><span class="sxs-lookup"><span data-stu-id="83c66-278">Let's get started.</span></span>

1. <span data-ttu-id="83c66-279">На панели **Иерархия** создайте новый пустой GameObject.</span><span class="sxs-lookup"><span data-stu-id="83c66-279">In the **Hierarchy** panel, create a new empty GameObject.</span></span> <span data-ttu-id="83c66-280">Назовите его "**астронаутманажер**".</span><span class="sxs-lookup"><span data-stu-id="83c66-280">Name it "**AstronautManager**".</span></span>
2. <span data-ttu-id="83c66-281">На панели **инспектора** нажмите кнопку **Добавить компонент** .</span><span class="sxs-lookup"><span data-stu-id="83c66-281">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="83c66-282">В меню введите **-космонавтам Manager** в поле поиска.</span><span class="sxs-lookup"><span data-stu-id="83c66-282">In the menu, type in the search box **Astronaut Manager**.</span></span> <span data-ttu-id="83c66-283">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="83c66-283">Select the search result.</span></span>
4. <span data-ttu-id="83c66-284">На панели **инспектора** нажмите кнопку **Добавить компонент** .</span><span class="sxs-lookup"><span data-stu-id="83c66-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
5. <span data-ttu-id="83c66-285">В меню введите в поле поиска **речевой вход источник**.</span><span class="sxs-lookup"><span data-stu-id="83c66-285">In the menu, type in the search box **Speech Input Source**.</span></span> <span data-ttu-id="83c66-286">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="83c66-286">Select the search result.</span></span>

<span data-ttu-id="83c66-287">Теперь мы добавим речевые команды, необходимые для управления состоянием взаимодействия-космонавтам.</span><span class="sxs-lookup"><span data-stu-id="83c66-287">We'll now add the speech commands required to control the interaction state of the astronaut.</span></span>

1. <span data-ttu-id="83c66-288">Разверните раздел **Ключевые слова** в **инспекторе**.</span><span class="sxs-lookup"><span data-stu-id="83c66-288">Expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="83c66-289">Щелкните в **+** правой части, чтобы добавить новое ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="83c66-289">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="83c66-290">Введите ключевое слово как **Move-космонавтам**.</span><span class="sxs-lookup"><span data-stu-id="83c66-290">Type the Keyword as **Move Astronaut**.</span></span> <span data-ttu-id="83c66-291">При необходимости вы можете добавить сочетание клавиш.</span><span class="sxs-lookup"><span data-stu-id="83c66-291">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="83c66-292">Щелкните в **+** правой части, чтобы добавить новое ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="83c66-292">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="83c66-293">Введите ключевое слово " **повернуть-космонавтам**".</span><span class="sxs-lookup"><span data-stu-id="83c66-293">Type the Keyword as **Rotate Astronaut**.</span></span> <span data-ttu-id="83c66-294">При необходимости вы можете добавить сочетание клавиш.</span><span class="sxs-lookup"><span data-stu-id="83c66-294">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="83c66-295">Соответствующий код обработчика можно найти в **GestureAction.CS** в обработчике **испичхандлер. онспичкэйвордрекогнизед** .</span><span class="sxs-lookup"><span data-stu-id="83c66-295">The corresponding handler code can be found in **GestureAction.cs**, in the **ISpeechHandler.OnSpeechKeywordRecognized** handler.</span></span>

![Настройка источника речевого ввода в главе 4](images/holograms211-speech.png)

<span data-ttu-id="83c66-297">Далее мы назовем обратную связь по манипуляции с курсором.</span><span class="sxs-lookup"><span data-stu-id="83c66-297">Next, we'll setup the manipulation feedback on the cursor.</span></span>

1. <span data-ttu-id="83c66-298">В папке **голограммы** на панели **проекта** найдите ресурс **пасингфидбакк** .</span><span class="sxs-lookup"><span data-stu-id="83c66-298">In the **Project** panel **Holograms** folder, find the **PathingFeedback** asset.</span></span>
2. <span data-ttu-id="83c66-299">Перетащите **пасингфидбакк** prefab на объект **курсорвисфидбакк** в **иерархии**.</span><span class="sxs-lookup"><span data-stu-id="83c66-299">Drag and drop the **PathingFeedback** prefab onto the **CursorWithFeedback** object in the **Hierarchy**.</span></span>
3. <span data-ttu-id="83c66-300">На панели **Иерархия** щелкните **курсорвисфидбакк**.</span><span class="sxs-lookup"><span data-stu-id="83c66-300">In the **Hierarchy** panel, click on **CursorWithFeedback**.</span></span>
4. <span data-ttu-id="83c66-301">Перетащите объект **пасингфидбакк** из **иерархии** на обнаруженное пользователем свойство **игрового объекта** в компоненте **обратной связи** в **инспекторе**.</span><span class="sxs-lookup"><span data-stu-id="83c66-301">Drag and drop the **PathingFeedback** object from the **Hierarchy** onto the **Pathing Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>

<span data-ttu-id="83c66-302">Теперь необходимо добавить код в **GestureAction.CS** , чтобы включить следующие возможности:</span><span class="sxs-lookup"><span data-stu-id="83c66-302">Now we need to add code to **GestureAction.cs** to enable the following:</span></span>

1. <span data-ttu-id="83c66-303">Добавьте код в функцию **иманипулатионхандлер. онманипулатионупдатед** , которая переместит-космонавтам при обнаружении жеста **манипуляции** .</span><span class="sxs-lookup"><span data-stu-id="83c66-303">Add code to the **IManipulationHandler.OnManipulationUpdated** function, which will move the astronaut when a **Manipulation** gesture is detected.</span></span>
2. <span data-ttu-id="83c66-304">Вычислите **вектор перемещения** , чтобы определить, куда следует переместить-космонавтам в зависимости от положения.</span><span class="sxs-lookup"><span data-stu-id="83c66-304">Calculate the **movement vector** to determine where the astronaut should be moved to based on hand position.</span></span>
3. <span data-ttu-id="83c66-305">**Переместите** -космонавтам в новое положение.</span><span class="sxs-lookup"><span data-stu-id="83c66-305">**Move** the astronaut to the new position.</span></span>

<span data-ttu-id="83c66-306">Завершите написание упражнения 4. a в **GestureAction.CS** или используйте наше завершенное решение ниже:</span><span class="sxs-lookup"><span data-stu-id="83c66-306">Complete coding exercise 4.a in **GestureAction.cs**, or use our completed solution below:</span></span>

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

### <a name="build-and-deploy"></a><span data-ttu-id="83c66-307">Построение и Развертывание</span><span class="sxs-lookup"><span data-stu-id="83c66-307">Build and Deploy</span></span>

* <span data-ttu-id="83c66-308">Перестройте в Unity, а затем выполните сборку и развертывание из Visual Studio, чтобы запустить приложение в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="83c66-308">Rebuild in Unity and then build and deploy from Visual Studio to run the app in HoloLens.</span></span>
* <span data-ttu-id="83c66-309">Переместите руку перед HoloLens и поднимите палец указателя, чтобы его можно было относить.</span><span class="sxs-lookup"><span data-stu-id="83c66-309">Move your hand in front of the HoloLens and raise your index finger so that it can be tracked.</span></span>
* <span data-ttu-id="83c66-310">Сосредоточьте курсор на-космонавтам.</span><span class="sxs-lookup"><span data-stu-id="83c66-310">Focus the cursor over the astronaut.</span></span>
* <span data-ttu-id="83c66-311">Скажите "Move-космонавтам", чтобы переместить-космонавтам с помощью жеста манипуляции.</span><span class="sxs-lookup"><span data-stu-id="83c66-311">Say 'Move Astronaut' to move the astronaut with a Manipulation gesture.</span></span>
* <span data-ttu-id="83c66-312">Вокруг курсора должны появиться четыре стрелки, чтобы показать, что программа будет реагировать на события манипуляции.</span><span class="sxs-lookup"><span data-stu-id="83c66-312">Four arrows should appear around the cursor to indicate that the program will now respond to Manipulation events.</span></span>
* <span data-ttu-id="83c66-313">Уменьшите индекс пальца до бегунка и сохраните их вместе.</span><span class="sxs-lookup"><span data-stu-id="83c66-313">Lower your index finger down to your thumb, and keep them pinched together.</span></span>
* <span data-ttu-id="83c66-314">Когда вы перемещаете свою руку,-космонавтам тоже перемещается (это манипуляция).</span><span class="sxs-lookup"><span data-stu-id="83c66-314">As you move your hand around, the astronaut will move too (this is Manipulation).</span></span>
* <span data-ttu-id="83c66-315">Поднимите указатель пальца, чтобы прерывать работу-космонавтам.</span><span class="sxs-lookup"><span data-stu-id="83c66-315">Raise your index finger to stop manipulating the astronaut.</span></span>
* <span data-ttu-id="83c66-316">Примечание. Если вы не говорите "Move-космонавтам" перед перемещением руки, вместо этого будет использоваться жест навигации.</span><span class="sxs-lookup"><span data-stu-id="83c66-316">Note: If you do not say 'Move Astronaut' before moving your hand, then the Navigation gesture will be used instead.</span></span>
* <span data-ttu-id="83c66-317">Скажите "повернуть-космонавтам", чтобы вернуться к состоянию ротатабле.</span><span class="sxs-lookup"><span data-stu-id="83c66-317">Say 'Rotate Astronaut' to return to the rotatable state.</span></span>

## <a name="chapter-5---model-expansion"></a><span data-ttu-id="83c66-318">Глава 5-расширение модели</span><span class="sxs-lookup"><span data-stu-id="83c66-318">Chapter 5 - Model expansion</span></span>

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a><span data-ttu-id="83c66-319">Цели</span><span class="sxs-lookup"><span data-stu-id="83c66-319">Objectives</span></span>

* <span data-ttu-id="83c66-320">Разверните модель-космонавтам на несколько небольших частей, с которыми может взаимодействовать пользователь.</span><span class="sxs-lookup"><span data-stu-id="83c66-320">Expand the Astronaut model into multiple, smaller pieces that the user can interact with.</span></span>
* <span data-ttu-id="83c66-321">Перемещение каждого элемента по отдельности с помощью жестов навигации и манипуляций.</span><span class="sxs-lookup"><span data-stu-id="83c66-321">Move each piece individually using Navigation and Manipulation gestures.</span></span>

### <a name="instructions"></a><span data-ttu-id="83c66-322">Инструкции</span><span class="sxs-lookup"><span data-stu-id="83c66-322">Instructions</span></span>

<span data-ttu-id="83c66-323">В этом разделе мы будем выполнять следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="83c66-323">In this section, we will accomplish the following tasks:</span></span>

1. <span data-ttu-id="83c66-324">Добавьте новое ключевое слово "**развернуть модель**", чтобы развернуть модель-космонавтам.</span><span class="sxs-lookup"><span data-stu-id="83c66-324">Add a new keyword "**Expand Model**" to expand the astronaut model.</span></span>
2. <span data-ttu-id="83c66-325">Добавьте новое ключевое слово "**сбросить модель**", чтобы вернуть модель в исходную форму.</span><span class="sxs-lookup"><span data-stu-id="83c66-325">Add a new Keyword "**Reset Model**" to return the model to its original form.</span></span>

<span data-ttu-id="83c66-326">Это делается путем добавления еще двух ключевых слов в источник речевого ввода из предыдущей главы.</span><span class="sxs-lookup"><span data-stu-id="83c66-326">We'll do this by adding two more keywords to the Speech Input Source from the previous chapter.</span></span> <span data-ttu-id="83c66-327">Мы также покажем другой способ для работы с событиями распознавания.</span><span class="sxs-lookup"><span data-stu-id="83c66-327">We'll also demonstrate another way to handle recognition events.</span></span>

1. <span data-ttu-id="83c66-328">Щелкните назад в **астронаутманажер** в **инспекторе** и разверните раздел **Ключевые слова** в **инспекторе**.</span><span class="sxs-lookup"><span data-stu-id="83c66-328">Click back on **AstronautManager** in the **Inspector** and expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="83c66-329">Щелкните в **+** правой части, чтобы добавить новое ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="83c66-329">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="83c66-330">Введите ключевое слово как **развернуть модель**.</span><span class="sxs-lookup"><span data-stu-id="83c66-330">Type the Keyword as **Expand Model**.</span></span> <span data-ttu-id="83c66-331">При необходимости вы можете добавить сочетание клавиш.</span><span class="sxs-lookup"><span data-stu-id="83c66-331">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="83c66-332">Щелкните в **+** правой части, чтобы добавить новое ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="83c66-332">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="83c66-333">Введите ключевое слово как **Сброс модели**.</span><span class="sxs-lookup"><span data-stu-id="83c66-333">Type the Keyword as **Reset Model**.</span></span> <span data-ttu-id="83c66-334">При необходимости вы можете добавить сочетание клавиш.</span><span class="sxs-lookup"><span data-stu-id="83c66-334">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="83c66-335">На панели **инспектора** нажмите кнопку **Добавить компонент** .</span><span class="sxs-lookup"><span data-stu-id="83c66-335">In the **Inspector** panel, click the **Add Component** button.</span></span>
7. <span data-ttu-id="83c66-336">В меню введите **обработчик речевого ввода** для поля поиска.</span><span class="sxs-lookup"><span data-stu-id="83c66-336">In the menu, type in the search box **Speech Input Handler**.</span></span> <span data-ttu-id="83c66-337">Выберите результат поиска.</span><span class="sxs-lookup"><span data-stu-id="83c66-337">Select the search result.</span></span>
8. <span data-ttu-id="83c66-338">Проверьте **глобальный прослушиватель**, так как мы хотим, чтобы эти команды работали независимо от GameObject, на который мы работаем.</span><span class="sxs-lookup"><span data-stu-id="83c66-338">Check **Is Global Listener**, since we want these commands to work regardless of the GameObject we're focusing.</span></span>
9. <span data-ttu-id="83c66-339">Нажмите кнопку **+** и выберите **развернуть модель** в раскрывающемся списке ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="83c66-339">Click the **+** button and select **Expand Model** from the Keyword dropdown.</span></span>
10. <span data-ttu-id="83c66-340">Щелкните в **+** разделе ответ и перетащите **Астронаутманажер** из **иерархии** в поле **None (Object) (нет (объект))** .</span><span class="sxs-lookup"><span data-stu-id="83c66-340">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
11. <span data-ttu-id="83c66-341">Теперь щелкните раскрывающийся список **без функции** , выберите **астронаутманажер**, а затем **експандмоделкомманд**.</span><span class="sxs-lookup"><span data-stu-id="83c66-341">Now, click the **No Function** dropdown, select **AstronautManager**, then **ExpandModelCommand**.</span></span>
12. <span data-ttu-id="83c66-342">Нажмите кнопку обработчик речевого ввода **+** и выберите **сбросить модель** из раскрывающегося списка ключевых слов.</span><span class="sxs-lookup"><span data-stu-id="83c66-342">Click the Speech Input Handler's **+** button and select **Reset Model** from the Keyword dropdown.</span></span>
13. <span data-ttu-id="83c66-343">Щелкните в **+** разделе ответ и перетащите **Астронаутманажер** из **иерархии** в поле **None (Object) (нет (объект))** .</span><span class="sxs-lookup"><span data-stu-id="83c66-343">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
14. <span data-ttu-id="83c66-344">Теперь щелкните раскрывающийся список **без функции** , выберите **астронаутманажер**, а затем **ресетмоделкомманд**.</span><span class="sxs-lookup"><span data-stu-id="83c66-344">Now, click the **No Function** dropdown, select **AstronautManager**, then **ResetModelCommand**.</span></span>

![Настройка источника речевого ввода и обработчика для главы 5](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a><span data-ttu-id="83c66-346">Построение и Развертывание</span><span class="sxs-lookup"><span data-stu-id="83c66-346">Build and Deploy</span></span>

* <span data-ttu-id="83c66-347">Тестирование</span><span class="sxs-lookup"><span data-stu-id="83c66-347">Try it!</span></span> <span data-ttu-id="83c66-348">Выполните сборку и развертывание приложения в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="83c66-348">Build and deploy the app to the HoloLens.</span></span>
* <span data-ttu-id="83c66-349">Например, **разверните модель** , чтобы увидеть развернутую модель-космонавтам.</span><span class="sxs-lookup"><span data-stu-id="83c66-349">Say **Expand Model** to see the expanded astronaut model.</span></span>
* <span data-ttu-id="83c66-350">Используйте **навигацию** для вращения отдельных частей-космонавтам масти.</span><span class="sxs-lookup"><span data-stu-id="83c66-350">Use **Navigation** to rotate individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="83c66-351">Скажем, **переместить-космонавтам** , а затем использовать **манипуляции** для перемещения отдельных частей-космонавтам масти.</span><span class="sxs-lookup"><span data-stu-id="83c66-351">Say **Move Astronaut** and then use **Manipulation** to move individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="83c66-352">Например, **поверните-космонавтам** , чтобы снова повернуть шашки.</span><span class="sxs-lookup"><span data-stu-id="83c66-352">Say **Rotate Astronaut** to rotate the pieces again.</span></span>
* <span data-ttu-id="83c66-353">Произнесите **Сброс модели** , чтобы вернуть-космонавтам к исходной форме.</span><span class="sxs-lookup"><span data-stu-id="83c66-353">Say **Reset Model** to return the astronaut to its original form.</span></span>

## <a name="the-end"></a><span data-ttu-id="83c66-354">Конец</span><span class="sxs-lookup"><span data-stu-id="83c66-354">The End</span></span>

<span data-ttu-id="83c66-355">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="83c66-355">Congratulations!</span></span> <span data-ttu-id="83c66-356">Теперь вы выполнили **Ввод MR 211: жест**.</span><span class="sxs-lookup"><span data-stu-id="83c66-356">You have now completed **MR Input 211: Gesture**.</span></span>

* <span data-ttu-id="83c66-357">Вы узнали, как обнаруживать события отслеживания, навигации и манипуляции, а также реагировать на них.</span><span class="sxs-lookup"><span data-stu-id="83c66-357">You know how to detect and respond to hand tracking, navigation and manipulation events.</span></span>
* <span data-ttu-id="83c66-358">Вы понимаете разницу между жестами навигации и манипуляциями.</span><span class="sxs-lookup"><span data-stu-id="83c66-358">You understand the difference between Navigation and Manipulation gestures.</span></span>
* <span data-ttu-id="83c66-359">Вы узнаете, как изменить курсор, чтобы обеспечить визуальную обратную связь при обнаружении руки, когда рука собирается потеряться и когда объект поддерживает различные взаимодействия (Навигация и манипуляция).</span><span class="sxs-lookup"><span data-stu-id="83c66-359">You know how to change the cursor to provide visual feedback for when a hand is detected, when a hand is about to be lost, and for when an object supports different interactions (Navigation vs Manipulation).</span></span>