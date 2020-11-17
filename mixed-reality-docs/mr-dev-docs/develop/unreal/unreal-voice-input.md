---
title: Речевой ввод
description: Руководство по настройке и использованию речевого ввода в HoloLens 2 и нереальном подсистеме
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, нереалный, Нереальный механизм 4, UE4, HoloLens 2, голосовый ввод, речевое распознавание, Смешанная реальность, разработка, функции, документация, руководства, голограмма, Разработка игр, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 79a6043511cc4658ae2451dd8aa6350d8e8037fe
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678783"
---
# <a name="voice-input-in-unreal"></a><span data-ttu-id="fcdef-104">Ввод голоса в нереальном режиме</span><span class="sxs-lookup"><span data-stu-id="fcdef-104">Voice Input in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="fcdef-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="fcdef-105">Overview</span></span>
<span data-ttu-id="fcdef-106">Речевой ввод в нереальном режиме позволяет взаимодействовать с голограммами без использования жестов руки и поддерживается только HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="fcdef-106">Voice input in Unreal allows you to interact with a hologram without having to use hand gestures and is only supported HoloLens 2.</span></span> <span data-ttu-id="fcdef-107">Несмотря на то, что голосовый ввод в HoloLens 2 работает с тем же механизмом, который поддерживает речь во всех других универсальных приложениях Windows, в нереальном режиме используется более ограниченный механизм для обработки голосового ввода.</span><span class="sxs-lookup"><span data-stu-id="fcdef-107">Even though voice input on HoloLens 2 is powered by the same engine that supports speech in all other Universal Windows Apps, Unreal uses a more limited engine of its own to process voice input.</span></span> <span data-ttu-id="fcdef-108">Это ограничивает возможности голосового ввода нереальными стандартными сопоставлениями речи, которые рассматриваются в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="fcdef-108">This limits voice input features in Unreal to predefined speech mappings, which is covered in the following sections.</span></span> 

## <a name="enabling-speech-recognition"></a><span data-ttu-id="fcdef-109">Включение распознавания речи</span><span class="sxs-lookup"><span data-stu-id="fcdef-109">Enabling Speech Recognition</span></span>

<span data-ttu-id="fcdef-110">Включение распознавания речи в HoloLens:</span><span class="sxs-lookup"><span data-stu-id="fcdef-110">To enable speech recognition on HoloLens:</span></span>
1. <span data-ttu-id="fcdef-111">Выберите **Параметры проекта > платформа > HoloLens >ные возможности** и включите **микрофон**.</span><span class="sxs-lookup"><span data-stu-id="fcdef-111">Select **Project Settings > Platform > HoloLens > Capabilities** and enable **Microphone**.</span></span> 
2. <span data-ttu-id="fcdef-112">Включено распознавание речи в **параметрах > конфиденциальность > речи** и выберите **Английский**.</span><span class="sxs-lookup"><span data-stu-id="fcdef-112">Enabled speech recognition in **Settings > Privacy > Speech** and select **English**.</span></span>

> [!NOTE]
> <span data-ttu-id="fcdef-113">Функция распознавания речи всегда работает на языке интерфейса Windows, настроенном в приложении " **Параметры** ".</span><span class="sxs-lookup"><span data-stu-id="fcdef-113">Speech recognition always functions in the Windows display language configured in the **Settings** app.</span></span> <span data-ttu-id="fcdef-114">Рекомендуется также включить **Распознавание речи в Интернете** , чтобы обеспечить лучшее качество обслуживания.</span><span class="sxs-lookup"><span data-stu-id="fcdef-114">It’s recommended that you also enable **Online speech recognition** for the best service quality.</span></span>

![Параметры распознавания речи Windows](images/unreal/speech-recognition-settings.png)

3. <span data-ttu-id="fcdef-116">При первом запуске приложения отобразится диалоговое окно с запросом на включение микрофона.</span><span class="sxs-lookup"><span data-stu-id="fcdef-116">A dialog will show up when the application first starts to ask if you want to enable the microphone.</span></span> <span data-ttu-id="fcdef-117">Выбор параметра **Да** запускает голосовое входное значение в приложении.</span><span class="sxs-lookup"><span data-stu-id="fcdef-117">Selecting **Yes** starts voice input in the app.</span></span>

<span data-ttu-id="fcdef-118">Речевой ввод не требует специальных интерфейсов API Windows Mixed Reality; Он основан на существующем API-интерфейсе сопоставления [входных данных](https://docs.unrealengine.com/Gameplay/Input/index.html) в нереального модуля 4.</span><span class="sxs-lookup"><span data-stu-id="fcdef-118">Voice input doesn’t require any special Windows Mixed Reality APIs; it's built on the existing Unreal Engine 4 [Input](https://docs.unrealengine.com/Gameplay/Input/index.html) mapping API.</span></span> 

## <a name="adding-speech-mappings"></a><span data-ttu-id="fcdef-119">Добавление сопоставлений речи</span><span class="sxs-lookup"><span data-stu-id="fcdef-119">Adding Speech Mappings</span></span>
<span data-ttu-id="fcdef-120">Подключение речи к действию является важным шагом при использовании голосового ввода.</span><span class="sxs-lookup"><span data-stu-id="fcdef-120">Connecting speech to action is an important step when using voice input.</span></span> <span data-ttu-id="fcdef-121">Эти сопоставления отслеживают ключевые слова приложения для речи, которые пользователь может сказать, а затем запускают связанное действие.</span><span class="sxs-lookup"><span data-stu-id="fcdef-121">These mappings monitor the app for speech keywords that a user might say, then fire off a linked action.</span></span> <span data-ttu-id="fcdef-122">Сопоставления речи можно найти, выполнив следующие действия.</span><span class="sxs-lookup"><span data-stu-id="fcdef-122">You can find Speech Mappings by:</span></span>
1. <span data-ttu-id="fcdef-123">Выберите **изменить > параметры проекта**, прокрутите до раздела **подсистема** и выберите **входные данные**.</span><span class="sxs-lookup"><span data-stu-id="fcdef-123">Selecting **Edit > Project Settings**, scrolling to the **Engine** section, and clicking **Input**.</span></span>

<span data-ttu-id="fcdef-124">Чтобы добавить новое сопоставление речи для команды перехода, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="fcdef-124">To add a new Speech Mapping for a jump command:</span></span>
1. <span data-ttu-id="fcdef-125">Щелкните **+** значок рядом с **элементом массив** и заполните следующие значения:</span><span class="sxs-lookup"><span data-stu-id="fcdef-125">Click the **+** icon next to **Array elements** and fill out the following values:</span></span>
    * <span data-ttu-id="fcdef-126">**жумпворд** для **имени действия**</span><span class="sxs-lookup"><span data-stu-id="fcdef-126">**jumpWord** for **Action Name**</span></span>
    * <span data-ttu-id="fcdef-127">**Перейти** к **ключевому слову речи**</span><span class="sxs-lookup"><span data-stu-id="fcdef-127">**jump** for **Speech Keyword**</span></span>

> [!NOTE]
> <span data-ttu-id="fcdef-128">В качестве ключевого слова можно использовать любые английские слова или короткие предложения.</span><span class="sxs-lookup"><span data-stu-id="fcdef-128">Any English word(s) or short sentence(s) can be used as a keyword.</span></span> 

![Входные параметры модуля UE4](images/unreal/engine-input.png)

<span data-ttu-id="fcdef-130">Сопоставления речи можно использовать в качестве входных компонентов, таких как сопоставление действий или осей, или как узлы схемы в графе событий.</span><span class="sxs-lookup"><span data-stu-id="fcdef-130">Speech Mappings can be used as Input components like Action or Axis Mappings or as blueprint nodes in the Event Graph.</span></span> <span data-ttu-id="fcdef-131">Например, можно связать команду перехода, чтобы напечатать два разных журнала в зависимости от того, когда речь идет об слове:</span><span class="sxs-lookup"><span data-stu-id="fcdef-131">For example, you could link the jump command to print out two different logs depending on when the word is spoken:</span></span>

1. <span data-ttu-id="fcdef-132">Дважды щелкните проект, чтобы открыть его в **графе событий**.</span><span class="sxs-lookup"><span data-stu-id="fcdef-132">Double-click a blueprint to open it in the **Event Graph**.</span></span>
2. <span data-ttu-id="fcdef-133">Щелкните **правой кнопкой мыши** и найдите **имя действия** для сопоставления речи (в данном случае это **жумпворд**), а затем нажмите клавишу **Ввод**.</span><span class="sxs-lookup"><span data-stu-id="fcdef-133">**Right-click** and search for the **Action Name** of your speech mapping (in this case **jumpWord**), then hit **Enter**.</span></span> <span data-ttu-id="fcdef-134">При этом на граф добавляется узел **входного действия** .</span><span class="sxs-lookup"><span data-stu-id="fcdef-134">This adds an **Input Action** node to the graph.</span></span>
3. <span data-ttu-id="fcdef-135">Перетащите выделенный ПИН **-** код для **печати строкового** узла, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="fcdef-135">Drag and drop the **Pressed** pin to **Print String** node as shown in the image below.</span></span> <span data-ttu-id="fcdef-136">**Освобожденный** ПИН-код можно оставить пустым, он не будет выполнять никаких действий для сопоставления речи.</span><span class="sxs-lookup"><span data-stu-id="fcdef-136">You can leave the **Released** pin empty, it won't execute anything for speech mappings.</span></span>
 
![Простое действие для голоса](images/unreal/voice-input-img-03.png)

4. <span data-ttu-id="fcdef-138">Воспроизводите приложение, скажем, **Переход** на слово и Просмотр консоли выводят журналы.</span><span class="sxs-lookup"><span data-stu-id="fcdef-138">Play the app, say the word **jump** and watch the console print out the logs!</span></span>

<span data-ttu-id="fcdef-139">Это все, что необходимо для того, чтобы добавить речевой ввод в приложения HoloLens в нереальном виде.</span><span class="sxs-lookup"><span data-stu-id="fcdef-139">That's all the setup you'll need to start adding voice input to your HoloLens apps in Unreal.</span></span> <span data-ttu-id="fcdef-140">Дополнительные сведения о речевых операциях и интерактивных действиях можно найти по ссылкам ниже, и не забудьте подумать о том, что вы создаете для пользователей.</span><span class="sxs-lookup"><span data-stu-id="fcdef-140">You can find more information on speech and interactivity can be found at the links below, and be sure to think about the experience you're creating for your users.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="fcdef-141">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="fcdef-141">Next Development Checkpoint</span></span>

<span data-ttu-id="fcdef-142">Если вы подготовились к нереальному пути к контрольной точке разработки, мы разработали следующие задачи: изучение возможностей платформы смешанной реальности и API-интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="fcdef-142">If you're following the Unreal development checkpoint journey we've laid out, you're next task is exploring the Mixed Reality platform capabilities and APIs:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="fcdef-143">Камера HoloLens</span><span class="sxs-lookup"><span data-stu-id="fcdef-143">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="fcdef-144">Вы можете в любой момент вернуться к [этапам разработки для Unreal](unreal-development-overview.md#2-core-building-blocks).</span><span class="sxs-lookup"><span data-stu-id="fcdef-144">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="fcdef-145">См. также статью</span><span class="sxs-lookup"><span data-stu-id="fcdef-145">See also</span></span>
* [<span data-ttu-id="fcdef-146">Речевой ввод</span><span class="sxs-lookup"><span data-stu-id="fcdef-146">Voice Input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="fcdef-147">Взгляд и фиксация</span><span class="sxs-lookup"><span data-stu-id="fcdef-147">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="fcdef-148">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="fcdef-148">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)

