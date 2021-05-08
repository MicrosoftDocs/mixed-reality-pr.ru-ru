---
title: Голосовой ввод в Unity
description: Узнайте, как Unity предоставляет три способа добавления голосового ввода, распознавания речи и диктовки в приложение Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Речевой ввод, Кэйвордрекогнизер, Граммаррекогнизер, микрофон, Диктовка, речь, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, МРТК, набор средств смешанной реальности
ms.openlocfilehash: 6b040443606e05843f85b2f74f5ea812daafba31
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489204"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="a174b-104">Голосовой ввод в Unity</span><span class="sxs-lookup"><span data-stu-id="a174b-104">Voice input in Unity</span></span>

> [!CAUTION]
> <span data-ttu-id="a174b-105">Прежде чем начать, рассмотрите возможность использования подключаемого модуля Unity для пакета SDK служб распознавания речи.</span><span class="sxs-lookup"><span data-stu-id="a174b-105">Before starting, consider using the Unity plug-in for the Cognitive Speech Services SDK.</span></span> <span data-ttu-id="a174b-106">У подключаемого модуля есть лучшие результаты для распознавания речи и простой доступ к декодированию речи в текст, а также расширенные функции речи, такие как диалоговое окно, взаимодействие на основе намерений, перевод, синтез текста в речь и распознавание речи на естественном языке.</span><span class="sxs-lookup"><span data-stu-id="a174b-106">The plugin has better Speech Accuracy results and easy access to speech-to-text decode, as well as advanced speech features like dialog, intent based interaction, translation, text-to-speech synthesis, and natural language speech recognition.</span></span> <span data-ttu-id="a174b-107">Чтобы приступить к работе, ознакомьтесь с [примером и документацией](/azure/cognitive-services/speech-service/quickstart-csharp-unity).</span><span class="sxs-lookup"><span data-stu-id="a174b-107">To get started, check out the [sample and documentation](/azure/cognitive-services/speech-service/quickstart-csharp-unity).</span></span>

<span data-ttu-id="a174b-108">Unity предоставляет три способа добавления [речевого ввода](../../design/voice-input.md) в приложение Unity, первые два из которых являются типами фрасерекогнизер:</span><span class="sxs-lookup"><span data-stu-id="a174b-108">Unity exposes three ways to add [Voice input](../../design/voice-input.md) to your Unity application, the first two of which are types of PhraseRecognizer:</span></span>
* <span data-ttu-id="a174b-109">`KeywordRecognizer`Предоставляет приложению массив строковых команд для прослушивания</span><span class="sxs-lookup"><span data-stu-id="a174b-109">The `KeywordRecognizer` supplies your app with an array of string commands to listen for</span></span>
* <span data-ttu-id="a174b-110">`GrammarRecognizer`Предоставляет приложению файл SRGS, определяющий конкретную грамматику для прослушивания</span><span class="sxs-lookup"><span data-stu-id="a174b-110">The `GrammarRecognizer` gives your app an SRGS file defining a specific grammar to listen for</span></span>
* <span data-ttu-id="a174b-111">`DictationRecognizer`Позволяет приложению прослушивать любое слово и предоставлять пользователю заметку или другое отображение речи</span><span class="sxs-lookup"><span data-stu-id="a174b-111">The `DictationRecognizer` lets your app listen for any word and provide the user with a note or other display of their speech</span></span>

> [!NOTE]
> <span data-ttu-id="a174b-112">Диктовка и распознавание фраз не могут быть обработаны одновременно.</span><span class="sxs-lookup"><span data-stu-id="a174b-112">Dictation and phrase recognition can't be handled at the same time.</span></span> <span data-ttu-id="a174b-113">Если Граммаррекогнизер или Кэйвордрекогнизер активен, Диктатионрекогнизер не может быть активным и наоборот.</span><span class="sxs-lookup"><span data-stu-id="a174b-113">If a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can't be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="a174b-114">Включение возможности для голоса</span><span class="sxs-lookup"><span data-stu-id="a174b-114">Enabling the capability for Voice</span></span>

<span data-ttu-id="a174b-115">Для использования речевого ввода приложение должно быть объявлено с помощью функции **микрофона** .</span><span class="sxs-lookup"><span data-stu-id="a174b-115">The **Microphone** capability must be declared for an app to use Voice input.</span></span>
1. <span data-ttu-id="a174b-116">В редакторе Unity выберите **правка > параметры проекта > проигрыватель** .</span><span class="sxs-lookup"><span data-stu-id="a174b-116">In the Unity Editor, navigate to **Edit > Project Settings > Player**</span></span>
2. <span data-ttu-id="a174b-117">Выберите вкладку " **Магазин Windows** "</span><span class="sxs-lookup"><span data-stu-id="a174b-117">Select the **Windows Store** tab</span></span>
3. <span data-ttu-id="a174b-118">В разделе " **Параметры публикации > возможности** " проверьте возможность использования **микрофона** .</span><span class="sxs-lookup"><span data-stu-id="a174b-118">In the **Publishing Settings > Capabilities** section, check the **Microphone** capability</span></span>
4. <span data-ttu-id="a174b-119">Предоставление разрешений приложению доступа к микрофону на устройстве HoloLens</span><span class="sxs-lookup"><span data-stu-id="a174b-119">Grant permissions to the app for microphone access on your HoloLens device</span></span>
    * <span data-ttu-id="a174b-120">Вам будет предложено сделать это при запуске устройства, но если вы случайно щелкнули "нет", вы можете изменить разрешения в параметрах устройства.</span><span class="sxs-lookup"><span data-stu-id="a174b-120">You'll be asked to do this on device startup, but if you accidentally clicked "no" you can change the permissions in the device settings</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="a174b-121">Распознавание фраз</span><span class="sxs-lookup"><span data-stu-id="a174b-121">Phrase Recognition</span></span>

<span data-ttu-id="a174b-122">Чтобы разрешить приложению прослушивать определенные фразы, произносимые пользователем, выполните некоторые действия:</span><span class="sxs-lookup"><span data-stu-id="a174b-122">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="a174b-123">Укажите, какие фразы следует прослушивать с помощью `KeywordRecognizer` или `GrammarRecognizer`</span><span class="sxs-lookup"><span data-stu-id="a174b-123">Specify which phrases to listen for using a `KeywordRecognizer` or `GrammarRecognizer`</span></span>
2. <span data-ttu-id="a174b-124">Обрабатывает `OnPhraseRecognized` событие и принимает действие, соответствующее распознанной фразе</span><span class="sxs-lookup"><span data-stu-id="a174b-124">Handle the `OnPhraseRecognized` event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="a174b-125">кэйвордрекогнизер</span><span class="sxs-lookup"><span data-stu-id="a174b-125">KeywordRecognizer</span></span>

<span data-ttu-id="a174b-126">**Пространство имен:** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="a174b-126">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="a174b-127">**Типы:** *кэйвордрекогнизер*, *фрасерекогнизедевентаргс*, *спичеррор*, *спичсистемстатус*</span><span class="sxs-lookup"><span data-stu-id="a174b-127">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="a174b-128">Чтобы сохранить несколько нажатий клавиш, потребуется несколько операторов using:</span><span class="sxs-lookup"><span data-stu-id="a174b-128">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="a174b-129">Затем добавим несколько полей в класс для хранения словаря распознавателя и ключевого слова >.</span><span class="sxs-lookup"><span data-stu-id="a174b-129">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="a174b-130">Теперь добавьте в словарь ключевое слово, например в `Start()` методе.</span><span class="sxs-lookup"><span data-stu-id="a174b-130">Now add a keyword to the dictionary, for example in of a `Start()` method.</span></span> <span data-ttu-id="a174b-131">В этом примере мы добавляем ключевое слово "Activate":</span><span class="sxs-lookup"><span data-stu-id="a174b-131">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="a174b-132">Создайте распознаватель ключевых слов и сообщите ему, что мы хотим узнать:</span><span class="sxs-lookup"><span data-stu-id="a174b-132">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="a174b-133">Теперь Зарегистрируйтесь для `OnPhraseRecognized` события</span><span class="sxs-lookup"><span data-stu-id="a174b-133">Now register for the `OnPhraseRecognized` event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="a174b-134">Пример обработчика:</span><span class="sxs-lookup"><span data-stu-id="a174b-134">An example handler is:</span></span>

```
private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    System.Action keywordAction;
    // if the keyword recognized is in our dictionary, call that Action.
    if (keywords.TryGetValue(args.text, out keywordAction))
    {
        keywordAction.Invoke();
    }
}
```

<span data-ttu-id="a174b-135">Наконец, начните распознать!</span><span class="sxs-lookup"><span data-stu-id="a174b-135">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="a174b-136">граммаррекогнизер</span><span class="sxs-lookup"><span data-stu-id="a174b-136">GrammarRecognizer</span></span>

<span data-ttu-id="a174b-137">**Пространство имен:** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="a174b-137">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="a174b-138">**Типы**: *граммаррекогнизер*, *фрасерекогнизедевентаргс*, *спичеррор*, *спичсистемстатус*</span><span class="sxs-lookup"><span data-stu-id="a174b-138">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="a174b-139">Граммаррекогнизер используется, если вы указываете грамматику для распознавания с помощью SRGS.</span><span class="sxs-lookup"><span data-stu-id="a174b-139">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="a174b-140">Это может быть полезно, если приложение содержит несколько ключевых слов, если вы хотите распознавать более сложные фразы или хотите легко включать и выключать наборы команд.</span><span class="sxs-lookup"><span data-stu-id="a174b-140">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="a174b-141">Сведения о формате файла см. [в статье Создание грамматик с помощью XML-кода SRGS](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) .</span><span class="sxs-lookup"><span data-stu-id="a174b-141">See: [Create Grammars Using SRGS XML](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) for file format information.</span></span>

<span data-ttu-id="a174b-142">После того как грамматика SRGS будет доступна в проекте в [папке стреамингассетс](https://docs.unity3d.com/Manual/StreamingAssets.html):</span><span class="sxs-lookup"><span data-stu-id="a174b-142">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](https://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="a174b-143">Создайте `GrammarRecognizer` и передайте ему путь к файлу SRGS:</span><span class="sxs-lookup"><span data-stu-id="a174b-143">Create a `GrammarRecognizer` and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="a174b-144">Теперь Зарегистрируйтесь для `OnPhraseRecognized` события</span><span class="sxs-lookup"><span data-stu-id="a174b-144">Now register for the `OnPhraseRecognized` event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="a174b-145">Вы получите обратный вызов, содержащий сведения, указанные в грамматике SRGS, которую можно правильно обойти.</span><span class="sxs-lookup"><span data-stu-id="a174b-145">You'll get a callback containing information specified in your SRGS grammar, which you can handle appropriately.</span></span> <span data-ttu-id="a174b-146">Большая часть важной информации будет предоставлена в `semanticMeanings` массиве.</span><span class="sxs-lookup"><span data-stu-id="a174b-146">Most of the important information will be provided in the `semanticMeanings` array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="a174b-147">Наконец, начните распознать!</span><span class="sxs-lookup"><span data-stu-id="a174b-147">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="a174b-148">Диктовка</span><span class="sxs-lookup"><span data-stu-id="a174b-148">Dictation</span></span>

<span data-ttu-id="a174b-149">**Пространство имен:** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="a174b-149">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="a174b-150">**Типы**: *диктатионрекогнизер*, *спичеррор*, *спичсистемстатус*</span><span class="sxs-lookup"><span data-stu-id="a174b-150">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="a174b-151">Используйте `DictationRecognizer` для преобразования речи пользователя в текст.</span><span class="sxs-lookup"><span data-stu-id="a174b-151">Use the `DictationRecognizer` to convert the user's speech to text.</span></span> <span data-ttu-id="a174b-152">Диктатионрекогнизер предоставляет функции [диктовки](../../design/voice-input.md#dictation) и поддерживает регистрацию и прослушивание событий завершения и фразы, поэтому вы можете отправить отзыв пользователю, когда они говорят и затем.</span><span class="sxs-lookup"><span data-stu-id="a174b-152">The DictationRecognizer exposes [dictation](../../design/voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="a174b-153">`Start()` методы и, `Stop()` соответственно, включают и отключают распознавание диктовки.</span><span class="sxs-lookup"><span data-stu-id="a174b-153">`Start()` and `Stop()` methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="a174b-154">После завершения с распознавателем его следует удалить с помощью, `Dispose()` чтобы освободить используемые ресурсы.</span><span class="sxs-lookup"><span data-stu-id="a174b-154">Once done with the recognizer, it should be disposed using `Dispose()` to release the resources it uses.</span></span> <span data-ttu-id="a174b-155">Он автоматически освобождает эти ресурсы во время сборки мусора при дополнительных затратах на производительность, если они не выявляются до этого.</span><span class="sxs-lookup"><span data-stu-id="a174b-155">It will release these resources automatically during garbage collection at an extra performance cost if they aren't released before that.</span></span>

<span data-ttu-id="a174b-156">Чтобы начать работу с диктовкой, необходимо выполнить несколько шагов.</span><span class="sxs-lookup"><span data-stu-id="a174b-156">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="a174b-157">Создать новый `DictationRecognizer`</span><span class="sxs-lookup"><span data-stu-id="a174b-157">Create a new `DictationRecognizer`</span></span>
2. <span data-ttu-id="a174b-158">Обработку событий диктовки</span><span class="sxs-lookup"><span data-stu-id="a174b-158">Handle Dictation events</span></span>
3. <span data-ttu-id="a174b-159">Запуск Диктатионрекогнизер</span><span class="sxs-lookup"><span data-stu-id="a174b-159">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="a174b-160">Включение функции для диктовки</span><span class="sxs-lookup"><span data-stu-id="a174b-160">Enabling the capability for dictation</span></span>

<span data-ttu-id="a174b-161">Для использования режима диктовки в приложении необходимо объявить **клиент Интернета** и возможности **микрофона** .</span><span class="sxs-lookup"><span data-stu-id="a174b-161">The **Internet Client** and **Microphone** capabilities must be declared for an app to use dictation:</span></span>
1. <span data-ttu-id="a174b-162">В редакторе Unity выберите **правка > параметры проекта > проигрыватель** .</span><span class="sxs-lookup"><span data-stu-id="a174b-162">In the Unity Editor, go to **Edit > Project Settings > Player**</span></span>
2. <span data-ttu-id="a174b-163">Выберите на вкладке " **Магазин Windows** "</span><span class="sxs-lookup"><span data-stu-id="a174b-163">Select on the **Windows Store** tab</span></span>
3. <span data-ttu-id="a174b-164">В разделе " **Параметры публикации > возможности** " проверьте возможность **InternetClient**</span><span class="sxs-lookup"><span data-stu-id="a174b-164">In the **Publishing Settings > Capabilities** section, check the **InternetClient** capability</span></span>
    * <span data-ttu-id="a174b-165">Кроме того, если микрофон еще не включен, проверьте возможность использования **микрофона** .</span><span class="sxs-lookup"><span data-stu-id="a174b-165">Optionally, if you didn't already enable the microphone, check the **Microphone** capability</span></span>
4. <span data-ttu-id="a174b-166">Предоставьте доступ к приложению для доступа к микрофону на устройстве HoloLens, если вы еще этого не сделали.</span><span class="sxs-lookup"><span data-stu-id="a174b-166">Grant permissions to the app for microphone access on your HoloLens device if you haven't already</span></span>
    * <span data-ttu-id="a174b-167">Вам будет предложено сделать это при запуске устройства, но если вы случайно щелкнули "нет", вы можете изменить разрешения в параметрах устройства.</span><span class="sxs-lookup"><span data-stu-id="a174b-167">You'll be asked to do this on device startup, but if you accidentally clicked "no" you can change the permissions in the device settings</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="a174b-168">диктатионрекогнизер</span><span class="sxs-lookup"><span data-stu-id="a174b-168">DictationRecognizer</span></span>

<span data-ttu-id="a174b-169">Создайте Диктатионрекогнизер следующим образом:</span><span class="sxs-lookup"><span data-stu-id="a174b-169">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="a174b-170">Существует четыре события диктовки, которые можно подписывать и обрабатывать для реализации поведения диктовки.</span><span class="sxs-lookup"><span data-stu-id="a174b-170">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. `DictationResult`
2. `DictationComplete`
3. `DictationHypothesis`
4. `DictationError`

<span data-ttu-id="a174b-171">**диктатионресулт**</span><span class="sxs-lookup"><span data-stu-id="a174b-171">**DictationResult**</span></span>

<span data-ttu-id="a174b-172">Это событие возникает после приостановки пользователем, как правило, в конце предложения.</span><span class="sxs-lookup"><span data-stu-id="a174b-172">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="a174b-173">Здесь возвращается полная распознанная строка.</span><span class="sxs-lookup"><span data-stu-id="a174b-173">The full recognized string is returned here.</span></span>

<span data-ttu-id="a174b-174">Сначала Подпишитесь на `DictationResult` событие:</span><span class="sxs-lookup"><span data-stu-id="a174b-174">First, subscribe to the `DictationResult` event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="a174b-175">Затем обработайте обратный вызов Диктатионресулт:</span><span class="sxs-lookup"><span data-stu-id="a174b-175">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="a174b-176">**диктатионхипосесис**</span><span class="sxs-lookup"><span data-stu-id="a174b-176">**DictationHypothesis**</span></span>

<span data-ttu-id="a174b-177">Это событие возникает постоянно во время разговора пользователя.</span><span class="sxs-lookup"><span data-stu-id="a174b-177">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="a174b-178">Как распознаватель прослушивает этот момент, он предоставляет текст о том, что он слышал.</span><span class="sxs-lookup"><span data-stu-id="a174b-178">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="a174b-179">Сначала Подпишитесь на `DictationHypothesis` событие:</span><span class="sxs-lookup"><span data-stu-id="a174b-179">First, subscribe to the `DictationHypothesis` event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="a174b-180">Затем обработайте обратный вызов Диктатионхипосесис:</span><span class="sxs-lookup"><span data-stu-id="a174b-180">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="a174b-181">**диктатионкомплете**</span><span class="sxs-lookup"><span data-stu-id="a174b-181">**DictationComplete**</span></span>

<span data-ttu-id="a174b-182">Это событие возникает при остановке распознавателя, при вызове из метода Stop (), истечения времени ожидания или при возникновении какой-либо другой ошибки.</span><span class="sxs-lookup"><span data-stu-id="a174b-182">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="a174b-183">Сначала Подпишитесь на `DictationComplete` событие:</span><span class="sxs-lookup"><span data-stu-id="a174b-183">First, subscribe to the `DictationComplete` event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="a174b-184">Затем обработайте обратный вызов Диктатионкомплете:</span><span class="sxs-lookup"><span data-stu-id="a174b-184">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="a174b-185">**диктатионеррор**</span><span class="sxs-lookup"><span data-stu-id="a174b-185">**DictationError**</span></span>

<span data-ttu-id="a174b-186">Это событие возникает при возникновении ошибки.</span><span class="sxs-lookup"><span data-stu-id="a174b-186">This event is fired when an error occurs.</span></span>

<span data-ttu-id="a174b-187">Сначала Подпишитесь на `DictationError` событие:</span><span class="sxs-lookup"><span data-stu-id="a174b-187">First, subscribe to the `DictationError` event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="a174b-188">Затем обработайте обратный вызов Диктатионеррор:</span><span class="sxs-lookup"><span data-stu-id="a174b-188">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="a174b-189">После подписки и обработки событий диктовки запустите распознаватель диктовки, чтобы начать получать события.</span><span class="sxs-lookup"><span data-stu-id="a174b-189">Once you've subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="a174b-190">Если вы больше не хотите поддерживать Диктатионрекогнизер, необходимо отменить подписывание событий и ликвидировать Диктатионрекогнизер.</span><span class="sxs-lookup"><span data-stu-id="a174b-190">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="a174b-191">**Советы**</span><span class="sxs-lookup"><span data-stu-id="a174b-191">**Tips**</span></span>
* <span data-ttu-id="a174b-192">`Start()` методы и, `Stop()` соответственно, включают и отключают распознавание диктовки.</span><span class="sxs-lookup"><span data-stu-id="a174b-192">`Start()` and `Stop()` methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="a174b-193">После завершения с распознавателем его необходимо удалить с помощью, `Dispose()` чтобы освободить используемые ресурсы.</span><span class="sxs-lookup"><span data-stu-id="a174b-193">Once done with the recognizer, it must be disposed using `Dispose()` to release the resources it uses.</span></span> <span data-ttu-id="a174b-194">Он автоматически освобождает эти ресурсы во время сборки мусора при дополнительных затратах на производительность, если они не выявляются до этого.</span><span class="sxs-lookup"><span data-stu-id="a174b-194">It will release these resources automatically during garbage collection at an extra performance cost if they aren't released before that.</span></span>
* <span data-ttu-id="a174b-195">Время ожидания происходит по истечении заданного периода времени.</span><span class="sxs-lookup"><span data-stu-id="a174b-195">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="a174b-196">Эти времена ожидания можно проверить в `DictationComplete` событии.</span><span class="sxs-lookup"><span data-stu-id="a174b-196">You can check for these timeouts in the `DictationComplete` event.</span></span> <span data-ttu-id="a174b-197">Существует два времени ожидания, которые следует учитывать:</span><span class="sxs-lookup"><span data-stu-id="a174b-197">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="a174b-198">Если распознаватель запускается и не слышит звук в течение первых пяти секунд, время ожидания истекает.</span><span class="sxs-lookup"><span data-stu-id="a174b-198">If the recognizer starts and doesn't hear any audio for the first five seconds, it will time out.</span></span>
   2. <span data-ttu-id="a174b-199">Если распознаватель предоставил результат, а затем слышит бездействия в течение 20 секунд, время ожидания истечет.</span><span class="sxs-lookup"><span data-stu-id="a174b-199">If the recognizer has given a result, but then hears silence for 20 seconds, it will time out.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="a174b-200">Использование распознавания и диктовки фраз</span><span class="sxs-lookup"><span data-stu-id="a174b-200">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="a174b-201">Если вы хотите использовать как распознавание, так и диктовку в приложении, необходимо полностью закрыть один из них, прежде чем можно будет начать другой.</span><span class="sxs-lookup"><span data-stu-id="a174b-201">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="a174b-202">Если вы используете несколько Кэйвордрекогнизерс, вы можете завершить их все одновременно с помощью:</span><span class="sxs-lookup"><span data-stu-id="a174b-202">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="a174b-203">Можно вызвать `Restart()` для восстановления всех распознавателей до их предыдущего состояния после остановки диктатионрекогнизер:</span><span class="sxs-lookup"><span data-stu-id="a174b-203">You can call `Restart()` to restore all recognizers to their previous state after the DictationRecognizer has stopped:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="a174b-204">Кроме того, можно просто запустить Кэйвордрекогнизер, который также перезапустит Фрасерекогнитионсистем.</span><span class="sxs-lookup"><span data-stu-id="a174b-204">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="a174b-205">Речевой ввод в наборе средств Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="a174b-205">Voice input in Mixed Reality Toolkit</span></span>

<span data-ttu-id="a174b-206">Примеры МРТК для речевого ввода можно найти в следующих демонстрационных сценах:</span><span class="sxs-lookup"><span data-stu-id="a174b-206">You can find MRTK examples for voice input in the following demo scenes:</span></span>
* [<span data-ttu-id="a174b-207">Диктовка</span><span class="sxs-lookup"><span data-stu-id="a174b-207">Dictation</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/Input/Scenes/Dictation)
* [<span data-ttu-id="a174b-208">Речь</span><span class="sxs-lookup"><span data-stu-id="a174b-208">Speech</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/Input/Scenes/Speech)

## <a name="next-development-checkpoint"></a><span data-ttu-id="a174b-209">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="a174b-209">Next Development Checkpoint</span></span>

<span data-ttu-id="a174b-210">Если вы используете точку контрольной точки разработки Unity, которую мы собрали, то вам следует ознакомиться с возможностями и API платформы смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="a174b-210">If you're following the Unity development checkpoint journey we've laid out, you're next task is exploring the Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="a174b-211">[общие возможности](shared-experiences-in-unity.md);</span><span class="sxs-lookup"><span data-stu-id="a174b-211">[Shared experiences](shared-experiences-in-unity.md)</span></span>

<span data-ttu-id="a174b-212">Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#2-core-building-blocks).</span><span class="sxs-lookup"><span data-stu-id="a174b-212">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>