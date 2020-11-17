---
title: Голосовой ввод в Unity
description: Unity предоставляет три способа добавления речевого ввода в приложение Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Речевой ввод, Кэйвордрекогнизер, Граммаррекогнизер, микрофон, Диктовка, речь, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, МРТК, набор средств смешанной реальности
ms.openlocfilehash: 20e2b8d4b8a18f38e72db7889a5d00cf15bfc0eb
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679893"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="d3301-104">Голосовой ввод в Unity</span><span class="sxs-lookup"><span data-stu-id="d3301-104">Voice input in Unity</span></span>

>[!NOTE]
><span data-ttu-id="d3301-105">Вместо приведенной ниже информации рассмотрите возможность использования подключаемого модуля Unity для пакета SDK служб распознавания речи, который обеспечивает гораздо более высокую точность результатов распознавания речи и предоставляет удобный доступ к декодированию речи в текст и расширенным функциям речи, таким как диалоговое окно, взаимодействие на основе намерения, перевод, синтез текста в речь и распознавание речи на естественном языке.</span><span class="sxs-lookup"><span data-stu-id="d3301-105">Instead of the below information, consider using the Unity plug-in for the Cognitive Speech Services SDK which has much better Speech Accuracy results and provides easy access to speech-to-text decode and advanced speech features like dialog, intent based interaction, translation, text-to-speech synthesis and natural language speech recognition.</span></span> <span data-ttu-id="d3301-106">Найдите пример и документация здесь: https://docs.microsoft.com//azure/cognitive-services/speech-service/quickstart-csharp-unity</span><span class="sxs-lookup"><span data-stu-id="d3301-106">Find the sample and documentaion here: https://docs.microsoft.com//azure/cognitive-services/speech-service/quickstart-csharp-unity</span></span>   

<span data-ttu-id="d3301-107">Unity предоставляет три способа добавления [речевого ввода](../../design/voice-input.md) в приложение Unity.</span><span class="sxs-lookup"><span data-stu-id="d3301-107">Unity exposes three ways to add [Voice input](../../design/voice-input.md) to your Unity application.</span></span>

<span data-ttu-id="d3301-108">При использовании Кэйвордрекогнизер (одного из двух типов Фрасерекогнизерс) приложению можно предоставить массив строк команд для прослушивания.</span><span class="sxs-lookup"><span data-stu-id="d3301-108">With the KeywordRecognizer (one of two types of PhraseRecognizers), your app can be given an array of string commands to listen for.</span></span> <span data-ttu-id="d3301-109">В Граммаррекогнизер (другой тип Фрасерекогнизер) приложению можно предоставить файл SRGS, определяющий конкретную грамматику для прослушивания.</span><span class="sxs-lookup"><span data-stu-id="d3301-109">With the GrammarRecognizer (the other type of PhraseRecognizer), your app can be given an SRGS file defining a specific grammar to listen for.</span></span> <span data-ttu-id="d3301-110">С помощью Диктатионрекогнизер приложение может прослушивать любое слово и предоставить пользователю заметку или другое отображение речи.</span><span class="sxs-lookup"><span data-stu-id="d3301-110">With the DictationRecognizer, your app can listen for any word and provide the user with a note or other display of their speech.</span></span>

>[!NOTE]
><span data-ttu-id="d3301-111">Одновременно можно обрабатывать только диктовку или распознавание фразы.</span><span class="sxs-lookup"><span data-stu-id="d3301-111">Only dictation or phrase recognition can be handled at once.</span></span> <span data-ttu-id="d3301-112">Это означает, что Граммаррекогнизер или Кэйвордрекогнизер активен, Диктатионрекогнизер не может быть активным и наоборот.</span><span class="sxs-lookup"><span data-stu-id="d3301-112">That means if a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can not be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="d3301-113">Включение возможности для голоса</span><span class="sxs-lookup"><span data-stu-id="d3301-113">Enabling the capability for Voice</span></span>

<span data-ttu-id="d3301-114">Чтобы использовать речевой ввод, для приложения необходимо объявить возможность использования **микрофона** .</span><span class="sxs-lookup"><span data-stu-id="d3301-114">The **Microphone** capability must be declared for an app to leverage Voice input.</span></span>
1. <span data-ttu-id="d3301-115">В редакторе Unity перейдите к параметрам проигрывателя, перейдя к разделу "изменение параметров проекта > > Player".</span><span class="sxs-lookup"><span data-stu-id="d3301-115">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
2. <span data-ttu-id="d3301-116">Перейдите на вкладку "Магазин Windows".</span><span class="sxs-lookup"><span data-stu-id="d3301-116">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="d3301-117">В разделе "Параметры публикации > возможности" проверьте возможность использования **микрофона** .</span><span class="sxs-lookup"><span data-stu-id="d3301-117">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="d3301-118">Распознавание фраз</span><span class="sxs-lookup"><span data-stu-id="d3301-118">Phrase Recognition</span></span>

<span data-ttu-id="d3301-119">Чтобы разрешить приложению прослушивать определенные фразы, произносимые пользователем, выполните некоторые действия:</span><span class="sxs-lookup"><span data-stu-id="d3301-119">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="d3301-120">Укажите, какие фразы следует прослушивать с помощью Кэйвордрекогнизер или Граммаррекогнизер</span><span class="sxs-lookup"><span data-stu-id="d3301-120">Specify which phrases to listen for using a KeywordRecognizer or GrammarRecognizer</span></span>
2. <span data-ttu-id="d3301-121">Обрабатывает событие Онфрасерекогнизед и принимает действие, соответствующее распознанной фразе</span><span class="sxs-lookup"><span data-stu-id="d3301-121">Handle the OnPhraseRecognized event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="d3301-122">кэйвордрекогнизер</span><span class="sxs-lookup"><span data-stu-id="d3301-122">KeywordRecognizer</span></span>

<span data-ttu-id="d3301-123">**Пространство имен:** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="d3301-123">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="d3301-124">**Типы:** *кэйвордрекогнизер*, *фрасерекогнизедевентаргс*, *спичеррор*, *спичсистемстатус*</span><span class="sxs-lookup"><span data-stu-id="d3301-124">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="d3301-125">Чтобы сохранить несколько нажатий клавиш, потребуется несколько операторов using:</span><span class="sxs-lookup"><span data-stu-id="d3301-125">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="d3301-126">Затем добавим несколько полей в класс для хранения словаря распознавателя и ключевого слова >.</span><span class="sxs-lookup"><span data-stu-id="d3301-126">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="d3301-127">Теперь добавьте в словарь ключевое слово (например, внутри метода Start ()).</span><span class="sxs-lookup"><span data-stu-id="d3301-127">Now add a keyword to the dictionary (e.g. inside of a Start() method).</span></span> <span data-ttu-id="d3301-128">В этом примере мы добавляем ключевое слово "Activate":</span><span class="sxs-lookup"><span data-stu-id="d3301-128">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="d3301-129">Создайте распознаватель ключевых слов и сообщите ему, что мы хотим узнать:</span><span class="sxs-lookup"><span data-stu-id="d3301-129">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="d3301-130">Теперь Зарегистрируйтесь для события Онфрасерекогнизед</span><span class="sxs-lookup"><span data-stu-id="d3301-130">Now register for the OnPhraseRecognized event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="d3301-131">Пример обработчика:</span><span class="sxs-lookup"><span data-stu-id="d3301-131">An example handler is:</span></span>

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

<span data-ttu-id="d3301-132">Наконец, начните распознать!</span><span class="sxs-lookup"><span data-stu-id="d3301-132">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="d3301-133">граммаррекогнизер</span><span class="sxs-lookup"><span data-stu-id="d3301-133">GrammarRecognizer</span></span>

<span data-ttu-id="d3301-134">**Пространство имен:** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="d3301-134">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="d3301-135">**Типы**: *граммаррекогнизер*, *фрасерекогнизедевентаргс*, *спичеррор*, *спичсистемстатус*</span><span class="sxs-lookup"><span data-stu-id="d3301-135">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="d3301-136">Граммаррекогнизер используется, если вы указываете грамматику для распознавания с помощью SRGS.</span><span class="sxs-lookup"><span data-stu-id="d3301-136">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="d3301-137">Это может быть полезно, если приложение содержит несколько ключевых слов, если вы хотите распознавать более сложные фразы или хотите легко включать и выключать наборы команд.</span><span class="sxs-lookup"><span data-stu-id="d3301-137">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="d3301-138">Сведения о формате файла см. [в статье Создание грамматик с помощью XML-кода SRGS](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) .</span><span class="sxs-lookup"><span data-stu-id="d3301-138">See: [Create Grammars Using SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) for file format information.</span></span>

<span data-ttu-id="d3301-139">После того как грамматика SRGS будет доступна в проекте в [папке стреамингассетс](https://docs.unity3d.com/Manual/StreamingAssets.html):</span><span class="sxs-lookup"><span data-stu-id="d3301-139">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](https://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="d3301-140">Создайте Граммаррекогнизер и передайте ему путь к файлу SRGS:</span><span class="sxs-lookup"><span data-stu-id="d3301-140">Create a GrammarRecognizer and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="d3301-141">Теперь Зарегистрируйтесь для события Онфрасерекогнизед</span><span class="sxs-lookup"><span data-stu-id="d3301-141">Now register for the OnPhraseRecognized event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="d3301-142">Вы получите обратный вызов, содержащий сведения, указанные в грамматике SRGS, которую можно будет правильно обойти.</span><span class="sxs-lookup"><span data-stu-id="d3301-142">You will get a callback containing information specified in your SRGS grammar which you can handle appropriately.</span></span> <span data-ttu-id="d3301-143">Большая часть важной информации будет предоставлена в массиве Семантикмеанингс.</span><span class="sxs-lookup"><span data-stu-id="d3301-143">Most of the important information will be provided in the semanticMeanings array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="d3301-144">Наконец, начните распознать!</span><span class="sxs-lookup"><span data-stu-id="d3301-144">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="d3301-145">Диктовка</span><span class="sxs-lookup"><span data-stu-id="d3301-145">Dictation</span></span>

<span data-ttu-id="d3301-146">**Пространство имен:** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="d3301-146">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="d3301-147">**Типы**: *диктатионрекогнизер*, *спичеррор*, *спичсистемстатус*</span><span class="sxs-lookup"><span data-stu-id="d3301-147">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="d3301-148">Используйте Диктатионрекогнизер для преобразования речи пользователя в текст.</span><span class="sxs-lookup"><span data-stu-id="d3301-148">Use the DictationRecognizer to convert the user's speech to text.</span></span> <span data-ttu-id="d3301-149">Диктатионрекогнизер предоставляет функции [диктовки](../../design/voice-input.md#dictation) и поддерживает регистрацию и прослушивание событий завершения и фразы, поэтому вы можете отправить отзыв пользователю, когда они говорят и затем.</span><span class="sxs-lookup"><span data-stu-id="d3301-149">The DictationRecognizer exposes [dictation](../../design/voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="d3301-150">Методы Start () и останавливают () соответственно включают и отключают распознавание диктовки.</span><span class="sxs-lookup"><span data-stu-id="d3301-150">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="d3301-151">После завершения с распознавателем его следует удалить с помощью метода Dispose (), чтобы освободить используемые ресурсы.</span><span class="sxs-lookup"><span data-stu-id="d3301-151">Once done with the recognizer, it should be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="d3301-152">Эти ресурсы будут автоматически освобождены во время сборки мусора при дополнительных затратах на производительность, если они не выводятся до этого.</span><span class="sxs-lookup"><span data-stu-id="d3301-152">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>

<span data-ttu-id="d3301-153">Чтобы начать работу с диктовкой, необходимо выполнить несколько шагов.</span><span class="sxs-lookup"><span data-stu-id="d3301-153">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="d3301-154">Создание нового Диктатионрекогнизер</span><span class="sxs-lookup"><span data-stu-id="d3301-154">Create a new DictationRecognizer</span></span>
2. <span data-ttu-id="d3301-155">Обработку событий диктовки</span><span class="sxs-lookup"><span data-stu-id="d3301-155">Handle Dictation events</span></span>
3. <span data-ttu-id="d3301-156">Запуск Диктатионрекогнизер</span><span class="sxs-lookup"><span data-stu-id="d3301-156">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="d3301-157">Включение функции для диктовки</span><span class="sxs-lookup"><span data-stu-id="d3301-157">Enabling the capability for dictation</span></span>

<span data-ttu-id="d3301-158">В дополнение к возможности "микрофона", упомянутой выше, необходимо объявить клиентский Интернет, чтобы использовать диктовку в приложении.</span><span class="sxs-lookup"><span data-stu-id="d3301-158">The "Internet Client" capability, in addition to the "Microphone" capability mentioned above, must be declared for an app to leverage dictation.</span></span>
1. <span data-ttu-id="d3301-159">В редакторе Unity перейдите к параметрам проигрывателя, перейдя на страницу "изменение > параметров проекта > Player".</span><span class="sxs-lookup"><span data-stu-id="d3301-159">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="d3301-160">Перейдите на вкладку "Магазин Windows".</span><span class="sxs-lookup"><span data-stu-id="d3301-160">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="d3301-161">В разделе "Параметры публикации > возможности" проверьте возможность **InternetClient**</span><span class="sxs-lookup"><span data-stu-id="d3301-161">In the "Publishing Settings > Capabilities" section, check the **InternetClient** capability</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="d3301-162">диктатионрекогнизер</span><span class="sxs-lookup"><span data-stu-id="d3301-162">DictationRecognizer</span></span>

<span data-ttu-id="d3301-163">Создайте Диктатионрекогнизер следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d3301-163">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="d3301-164">Существует четыре события диктовки, которые можно подписывать и обрабатывать для реализации поведения диктовки.</span><span class="sxs-lookup"><span data-stu-id="d3301-164">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. <span data-ttu-id="d3301-165">диктатионресулт</span><span class="sxs-lookup"><span data-stu-id="d3301-165">DictationResult</span></span>
2. <span data-ttu-id="d3301-166">диктатионкомплете</span><span class="sxs-lookup"><span data-stu-id="d3301-166">DictationComplete</span></span>
3. <span data-ttu-id="d3301-167">диктатионхипосесис</span><span class="sxs-lookup"><span data-stu-id="d3301-167">DictationHypothesis</span></span>
4. <span data-ttu-id="d3301-168">диктатионеррор</span><span class="sxs-lookup"><span data-stu-id="d3301-168">DictationError</span></span>

<span data-ttu-id="d3301-169">**диктатионресулт**</span><span class="sxs-lookup"><span data-stu-id="d3301-169">**DictationResult**</span></span>

<span data-ttu-id="d3301-170">Это событие возникает после приостановки пользователем, как правило, в конце предложения.</span><span class="sxs-lookup"><span data-stu-id="d3301-170">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="d3301-171">Здесь возвращается полная распознанная строка.</span><span class="sxs-lookup"><span data-stu-id="d3301-171">The full recognized string is returned here.</span></span>

<span data-ttu-id="d3301-172">Сначала Подпишитесь на событие Диктатионресулт:</span><span class="sxs-lookup"><span data-stu-id="d3301-172">First, subscribe to the DictationResult event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="d3301-173">Затем обработайте обратный вызов Диктатионресулт:</span><span class="sxs-lookup"><span data-stu-id="d3301-173">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="d3301-174">**диктатионхипосесис**</span><span class="sxs-lookup"><span data-stu-id="d3301-174">**DictationHypothesis**</span></span>

<span data-ttu-id="d3301-175">Это событие возникает постоянно во время разговора пользователя.</span><span class="sxs-lookup"><span data-stu-id="d3301-175">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="d3301-176">Как распознаватель прослушивает этот момент, он предоставляет текст о том, что он слышал.</span><span class="sxs-lookup"><span data-stu-id="d3301-176">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="d3301-177">Сначала Подпишитесь на событие Диктатионхипосесис:</span><span class="sxs-lookup"><span data-stu-id="d3301-177">First, subscribe to the DictationHypothesis event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="d3301-178">Затем обработайте обратный вызов Диктатионхипосесис:</span><span class="sxs-lookup"><span data-stu-id="d3301-178">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="d3301-179">**диктатионкомплете**</span><span class="sxs-lookup"><span data-stu-id="d3301-179">**DictationComplete**</span></span>

<span data-ttu-id="d3301-180">Это событие возникает при остановке распознавателя, при вызове из метода Stop (), истечения времени ожидания или при возникновении какой-либо другой ошибки.</span><span class="sxs-lookup"><span data-stu-id="d3301-180">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="d3301-181">Сначала Подпишитесь на событие Диктатионкомплете:</span><span class="sxs-lookup"><span data-stu-id="d3301-181">First, subscribe to the DictationComplete event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="d3301-182">Затем обработайте обратный вызов Диктатионкомплете:</span><span class="sxs-lookup"><span data-stu-id="d3301-182">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="d3301-183">**диктатионеррор**</span><span class="sxs-lookup"><span data-stu-id="d3301-183">**DictationError**</span></span>

<span data-ttu-id="d3301-184">Это событие возникает при возникновении ошибки.</span><span class="sxs-lookup"><span data-stu-id="d3301-184">This event is fired when an error occurs.</span></span>

<span data-ttu-id="d3301-185">Сначала Подпишитесь на событие Диктатионеррор:</span><span class="sxs-lookup"><span data-stu-id="d3301-185">First, subscribe to the DictationError event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="d3301-186">Затем обработайте обратный вызов Диктатионеррор:</span><span class="sxs-lookup"><span data-stu-id="d3301-186">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="d3301-187">После подписки и обработки событий диктовки запустите распознаватель диктовки, чтобы начать получать события.</span><span class="sxs-lookup"><span data-stu-id="d3301-187">Once you have subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="d3301-188">Если вы больше не хотите поддерживать Диктатионрекогнизер, необходимо отменить подписывание событий и ликвидировать Диктатионрекогнизер.</span><span class="sxs-lookup"><span data-stu-id="d3301-188">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="d3301-189">**Советы**</span><span class="sxs-lookup"><span data-stu-id="d3301-189">**Tips**</span></span>
* <span data-ttu-id="d3301-190">Методы Start () и останавливают () соответственно включают и отключают распознавание диктовки.</span><span class="sxs-lookup"><span data-stu-id="d3301-190">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="d3301-191">После завершения с распознавателем его необходимо удалить с помощью метода Dispose (), чтобы освободить используемые ресурсы.</span><span class="sxs-lookup"><span data-stu-id="d3301-191">Once done with the recognizer, it must be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="d3301-192">Эти ресурсы будут автоматически освобождены во время сборки мусора при дополнительных затратах на производительность, если они не выводятся до этого.</span><span class="sxs-lookup"><span data-stu-id="d3301-192">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>
* <span data-ttu-id="d3301-193">Время ожидания происходит по истечении заданного периода времени.</span><span class="sxs-lookup"><span data-stu-id="d3301-193">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="d3301-194">Эти времена ожидания можно проверить в событии Диктатионкомплете.</span><span class="sxs-lookup"><span data-stu-id="d3301-194">You can check for these timeouts in the DictationComplete event.</span></span> <span data-ttu-id="d3301-195">Существует два времени ожидания, которые следует учитывать:</span><span class="sxs-lookup"><span data-stu-id="d3301-195">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="d3301-196">Если распознаватель запускается и не слышит звук в течение первых пяти секунд, время ожидания истечет.</span><span class="sxs-lookup"><span data-stu-id="d3301-196">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
   2. <span data-ttu-id="d3301-197">Если распознаватель предоставил результат, а затем слышит бездействия в течение двадцати секунд, время ожидания истечет.</span><span class="sxs-lookup"><span data-stu-id="d3301-197">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="d3301-198">Использование распознавания и диктовки фраз</span><span class="sxs-lookup"><span data-stu-id="d3301-198">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="d3301-199">Если вы хотите использовать как распознавание, так и диктовку в приложении, необходимо полностью закрыть один из них, прежде чем можно будет начать другой.</span><span class="sxs-lookup"><span data-stu-id="d3301-199">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="d3301-200">Если вы используете несколько Кэйвордрекогнизерс, вы можете завершить их все одновременно с помощью:</span><span class="sxs-lookup"><span data-stu-id="d3301-200">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="d3301-201">Чтобы восстановить все распознаватели до их предыдущего состояния, после остановки Диктатионрекогнизер можно вызвать:</span><span class="sxs-lookup"><span data-stu-id="d3301-201">In order to restore all recognizers to their previous state, after the DictationRecognizer has stopped, you can call:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="d3301-202">Кроме того, можно просто запустить Кэйвордрекогнизер, который также перезапустит Фрасерекогнитионсистем.</span><span class="sxs-lookup"><span data-stu-id="d3301-202">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="using-the-microphone-helper"></a><span data-ttu-id="d3301-203">Использование вспомогательного метода микрофона</span><span class="sxs-lookup"><span data-stu-id="d3301-203">Using the microphone helper</span></span>

<span data-ttu-id="d3301-204">Набор средств Mixed Reality в GitHub содержит вспомогательный класс микрофона для указания разработчикам, если в системе есть пригодный для использования микрофон.</span><span class="sxs-lookup"><span data-stu-id="d3301-204">The Mixed Reality Toolkit on GitHub contains a microphone helper class to hint at developers if there is a usable microphone on the system.</span></span> <span data-ttu-id="d3301-205">Одним из них является необходимость проверки наличия микрофона в системе перед отображением любых подсказок речевого взаимодействия в приложении.</span><span class="sxs-lookup"><span data-stu-id="d3301-205">One use for it is where one would want to check if there is microphone on system before showing any speech interaction hints in the application.</span></span>

<span data-ttu-id="d3301-206">Вспомогательный сценарий микрофона можно найти в [папке input/Scripts/Utilities](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span><span class="sxs-lookup"><span data-stu-id="d3301-206">The microphone helper script can be found in the [Input/Scripts/Utilities folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span></span> <span data-ttu-id="d3301-207">Репозиторий GitHub также содержит [небольшой пример](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) , демонстрирующий использование вспомогательного метода.</span><span class="sxs-lookup"><span data-stu-id="d3301-207">The GitHub repo also contains a [small sample](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) demonstrating how to use the helper.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="d3301-208">Речевой ввод в наборе средств Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="d3301-208">Voice input in Mixed Reality Toolkit</span></span>
<span data-ttu-id="d3301-209">Примеры речевого ввода можно найти в этой сцене.</span><span class="sxs-lookup"><span data-stu-id="d3301-209">You can find the examples of the voice input in this scene.</span></span>

- [<span data-ttu-id="d3301-210">Холотулкит-ексамплес/input/сцены/Спичинпутсаурце. Unity</span><span class="sxs-lookup"><span data-stu-id="d3301-210">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)

## <a name="next-development-checkpoint"></a><span data-ttu-id="d3301-211">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="d3301-211">Next Development Checkpoint</span></span>

<span data-ttu-id="d3301-212">Если вы используете точку контрольной точки разработки Unity, которую мы собрали, то вам следует ознакомиться с возможностями и API платформы смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="d3301-212">If you're following the Unity development checkpoint journey we've laid out, you're next task is exploring the Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="d3301-213">[общие возможности](shared-experiences-in-unity.md);</span><span class="sxs-lookup"><span data-stu-id="d3301-213">[Shared experiences](shared-experiences-in-unity.md)</span></span>

<span data-ttu-id="d3301-214">Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#2-core-building-blocks).</span><span class="sxs-lookup"><span data-stu-id="d3301-214">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>
