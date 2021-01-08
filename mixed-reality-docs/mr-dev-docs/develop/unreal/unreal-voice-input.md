---
title: Ввод голоса в нереальном режиме
description: Узнайте, как настроить и использовать голосовой ввод, сопоставления речи и распознавание в нереальных приложениях смешанной реальности для устройств HoloLens 2.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, нереалный, Нереальный механизм 4, UE4, HoloLens 2, голосовый ввод, речевое распознавание, Смешанная реальность, разработка, функции, документация, руководства, голограмма, Разработка игр, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: c7ac523258dc44aa261470aea8cdf21f32c915b2
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010074"
---
# <a name="voice-input-in-unreal"></a><span data-ttu-id="44d5f-104">Ввод голоса в нереальном режиме</span><span class="sxs-lookup"><span data-stu-id="44d5f-104">Voice Input in Unreal</span></span>

<span data-ttu-id="44d5f-105">Речевой ввод в нереальном режиме позволяет взаимодействовать с голограммами без использования жестов руки и поддерживается только HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="44d5f-105">Voice input in Unreal allows you to interact with a hologram without having to use hand gestures and is only supported HoloLens 2.</span></span> <span data-ttu-id="44d5f-106">Голосовый ввод в HoloLens 2 питается на основе того же механизма, который поддерживает речь во всех других универсальных приложениях Windows, но нереально использует более ограниченный механизм для обработки голосовых данных.</span><span class="sxs-lookup"><span data-stu-id="44d5f-106">Voice input on HoloLens 2 is powered by the same engine that supports speech in all other Universal Windows Apps, but Unreal uses a more limited engine to process voice input.</span></span> <span data-ttu-id="44d5f-107">Это ограничивает возможности голосового ввода нереальными стандартными сопоставлениями речи, которые описаны в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="44d5f-107">This limits voice input features in Unreal to predefined speech mappings, which are covered in the following sections.</span></span> 

## <a name="enabling-speech-recognition"></a><span data-ttu-id="44d5f-108">Включение распознавания речи</span><span class="sxs-lookup"><span data-stu-id="44d5f-108">Enabling Speech Recognition</span></span>

<span data-ttu-id="44d5f-109">Включение распознавания речи в HoloLens:</span><span class="sxs-lookup"><span data-stu-id="44d5f-109">To enable speech recognition on HoloLens:</span></span>
1. <span data-ttu-id="44d5f-110">Выберите **Параметры проекта > платформа > HoloLens >ные возможности** и включите **микрофон**.</span><span class="sxs-lookup"><span data-stu-id="44d5f-110">Select **Project Settings > Platform > HoloLens > Capabilities** and enable **Microphone**.</span></span> 
2. <span data-ttu-id="44d5f-111">Включено распознавание речи в **параметрах > конфиденциальность > речи** и выберите **Английский**.</span><span class="sxs-lookup"><span data-stu-id="44d5f-111">Enabled speech recognition in **Settings > Privacy > Speech** and select **English**.</span></span>

> [!NOTE]
> <span data-ttu-id="44d5f-112">Функция распознавания речи всегда работает на языке интерфейса Windows, настроенном в приложении " **Параметры** ".</span><span class="sxs-lookup"><span data-stu-id="44d5f-112">Speech recognition always functions in the Windows display language configured in the **Settings** app.</span></span> <span data-ttu-id="44d5f-113">Рекомендуется также включить **Распознавание речи в Интернете** , чтобы обеспечить лучшее качество обслуживания.</span><span class="sxs-lookup"><span data-stu-id="44d5f-113">It’s recommended that you also enable **Online speech recognition** for the best service quality.</span></span>

![Параметры распознавания речи Windows](images/unreal/speech-recognition-settings.png)

3. <span data-ttu-id="44d5f-115">При первом запуске приложения отобразится диалоговое окно с запросом на включение микрофона.</span><span class="sxs-lookup"><span data-stu-id="44d5f-115">A dialog will show up when the application first starts to ask if you want to enable the microphone.</span></span> <span data-ttu-id="44d5f-116">Выбор параметра **Да** запускает голосовое входное значение в приложении.</span><span class="sxs-lookup"><span data-stu-id="44d5f-116">Selecting **Yes** starts voice input in the app.</span></span>

<span data-ttu-id="44d5f-117">Речевой ввод не требует специальных интерфейсов API Windows Mixed Reality; Он основан на существующем API-интерфейсе сопоставления [входных данных](https://docs.unrealengine.com/Gameplay/Input/index.html) в нереального модуля 4.</span><span class="sxs-lookup"><span data-stu-id="44d5f-117">Voice input doesn’t require any special Windows Mixed Reality APIs; it's built on the existing Unreal Engine 4 [Input](https://docs.unrealengine.com/Gameplay/Input/index.html) mapping API.</span></span> 

## <a name="adding-speech-mappings"></a><span data-ttu-id="44d5f-118">Добавление сопоставлений речи</span><span class="sxs-lookup"><span data-stu-id="44d5f-118">Adding Speech Mappings</span></span>

<span data-ttu-id="44d5f-119">Подключение речи к действию является важным шагом при использовании голосового ввода.</span><span class="sxs-lookup"><span data-stu-id="44d5f-119">Connecting speech to action is an important step when using voice input.</span></span> <span data-ttu-id="44d5f-120">Эти сопоставления отслеживают ключевые слова приложения для речи, которые пользователь может сказать, а затем запускают связанное действие.</span><span class="sxs-lookup"><span data-stu-id="44d5f-120">These mappings monitor the app for speech keywords that a user might say, then fire off a linked action.</span></span> <span data-ttu-id="44d5f-121">Сопоставления речи можно найти, выполнив следующие действия.</span><span class="sxs-lookup"><span data-stu-id="44d5f-121">You can find Speech Mappings by:</span></span>
1. <span data-ttu-id="44d5f-122">Выберите **изменить > параметры проекта**, прокрутите до раздела **подсистема** и выберите **входные данные**.</span><span class="sxs-lookup"><span data-stu-id="44d5f-122">Selecting **Edit > Project Settings**, scrolling to the **Engine** section, and clicking **Input**.</span></span>

<span data-ttu-id="44d5f-123">Чтобы добавить новое сопоставление речи для команды перехода, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="44d5f-123">To add a new Speech Mapping for a jump command:</span></span>
1. <span data-ttu-id="44d5f-124">Щелкните **+** значок рядом с **элементом массив** и заполните следующие значения:</span><span class="sxs-lookup"><span data-stu-id="44d5f-124">Select the **+** icon next to **Array elements** and fill out the following values:</span></span>
    * <span data-ttu-id="44d5f-125">**жумпворд** для **имени действия**</span><span class="sxs-lookup"><span data-stu-id="44d5f-125">**jumpWord** for **Action Name**</span></span>
    * <span data-ttu-id="44d5f-126">**Перейти** к **ключевому слову речи**</span><span class="sxs-lookup"><span data-stu-id="44d5f-126">**jump** for **Speech Keyword**</span></span>

> [!NOTE]
> <span data-ttu-id="44d5f-127">В качестве ключевого слова можно использовать любые английские слова или короткие предложения.</span><span class="sxs-lookup"><span data-stu-id="44d5f-127">Any English word(s) or short sentence(s) can be used as a keyword.</span></span> 

![Входные параметры модуля UE4](images/unreal/engine-input.png)

<span data-ttu-id="44d5f-129">Сопоставления речи можно использовать в качестве входных компонентов, таких как сопоставление действий или осей, или как узлы схемы в графе событий.</span><span class="sxs-lookup"><span data-stu-id="44d5f-129">Speech Mappings can be used as Input components like Action or Axis Mappings or as blueprint nodes in the Event Graph.</span></span> <span data-ttu-id="44d5f-130">Например, можно связать команду перехода, чтобы напечатать два разных журнала в зависимости от того, когда речь идет об слове:</span><span class="sxs-lookup"><span data-stu-id="44d5f-130">For example, you could link the jump command to print out two different logs depending on when the word is spoken:</span></span>

1. <span data-ttu-id="44d5f-131">Дважды щелкните проект, чтобы открыть его в **графе событий**.</span><span class="sxs-lookup"><span data-stu-id="44d5f-131">Double-click a blueprint to open it in the **Event Graph**.</span></span>
2. <span data-ttu-id="44d5f-132">Щелкните **правой кнопкой мыши** и найдите **имя действия** для сопоставления речи (в данном случае это **жумпворд**), а затем нажмите клавишу **Ввод** , чтобы добавить узел **входного действия** в граф.</span><span class="sxs-lookup"><span data-stu-id="44d5f-132">**Right-click** and search for the **Action Name** of your speech mapping (in this case **jumpWord**), then hit **Enter** to add an **Input Action** node to the graph.</span></span>
3. <span data-ttu-id="44d5f-133">Перетащите выделенный ПИН **-** код для **печати строкового** узла, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="44d5f-133">Drag and drop the **Pressed** pin to **Print String** node as shown in the image below.</span></span> <span data-ttu-id="44d5f-134">**Освобожденный** ПИН-код можно оставить пустым, он не будет выполнять никаких действий для сопоставления речи.</span><span class="sxs-lookup"><span data-stu-id="44d5f-134">You can leave the **Released** pin empty, it won't execute anything for speech mappings.</span></span>
 
![Простое действие для голоса](images/unreal/voice-input-img-03.png)

4. <span data-ttu-id="44d5f-136">Воспроизводите приложение, скажем, **Переходя** по слову и посмотрите, что консоль печатает журналы!</span><span class="sxs-lookup"><span data-stu-id="44d5f-136">Play the app, say the word **jump**, and watch the console print out the logs!</span></span>

<span data-ttu-id="44d5f-137">Это все, что необходимо для того, чтобы добавить речевой ввод в приложения HoloLens в нереальном виде.</span><span class="sxs-lookup"><span data-stu-id="44d5f-137">That's all the setup you'll need to start adding voice input to your HoloLens apps in Unreal.</span></span> <span data-ttu-id="44d5f-138">Дополнительные сведения о речевых операциях и интерактивных действиях см. в приведенных ниже ссылках, а также о том, что вы создаете для пользователей.</span><span class="sxs-lookup"><span data-stu-id="44d5f-138">You can find more information on speech and interactivity at the links below, and be sure to think about the experience you're creating for your users.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="44d5f-139">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="44d5f-139">Next Development Checkpoint</span></span>

<span data-ttu-id="44d5f-140">Если вы подготовились к нереальному разработку, мы разработали следующие задачи: изучение возможностей платформы смешанной реальности и API-интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="44d5f-140">If you're following the Unreal development journey we've laid out, you're next task is exploring the Mixed Reality platform capabilities and APIs:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="44d5f-141">Камера HoloLens</span><span class="sxs-lookup"><span data-stu-id="44d5f-141">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="44d5f-142">Вы можете в любой момент вернуться к [этапам разработки для Unreal](unreal-development-overview.md#2-core-building-blocks).</span><span class="sxs-lookup"><span data-stu-id="44d5f-142">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="44d5f-143">См. также статью</span><span class="sxs-lookup"><span data-stu-id="44d5f-143">See also</span></span>
* [<span data-ttu-id="44d5f-144">Речевой ввод</span><span class="sxs-lookup"><span data-stu-id="44d5f-144">Voice Input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="44d5f-145">Взгляд и фиксация</span><span class="sxs-lookup"><span data-stu-id="44d5f-145">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="44d5f-146">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="44d5f-146">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)

