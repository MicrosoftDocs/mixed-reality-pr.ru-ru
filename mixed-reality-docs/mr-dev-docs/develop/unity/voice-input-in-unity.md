---
title: Голосовой ввод в Unity
description: Узнайте, как Unity предоставляет три способа добавления голосового ввода, распознавания речи и диктовки в приложение Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Речевой ввод, Кэйвордрекогнизер, Граммаррекогнизер, микрофон, Диктовка, речь, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, МРТК, набор средств смешанной реальности
ms.openlocfilehash: c062289a1a26365528a86761b6b68a9a24041f7c
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550384"
---
# <a name="voice-input-in-unity"></a>Голосовой ввод в Unity

> [!CAUTION]
> Прежде чем начать, рассмотрите возможность использования подключаемого модуля Unity для пакета SDK служб распознавания речи. У подключаемого модуля есть лучшие результаты для распознавания речи и простой доступ к декодированию речи в текст, а также расширенные функции речи, такие как диалоговое окно, взаимодействие на основе намерений, перевод, синтез текста в речь и распознавание речи на естественном языке. Чтобы приступить к работе, ознакомьтесь с [примером и документацией](/azure/cognitive-services/speech-service/quickstart-csharp-unity).

Unity предоставляет три способа добавления [речевого ввода](../../design/voice-input.md) в приложение Unity, первые два из которых являются типами фрасерекогнизер:
* `KeywordRecognizer`Предоставляет приложению массив строковых команд для прослушивания
* `GrammarRecognizer`Предоставляет приложению файл SRGS, определяющий конкретную грамматику для прослушивания
* `DictationRecognizer`Позволяет приложению прослушивать любое слово и предоставлять пользователю заметку или другое отображение речи

> [!NOTE]
> Диктовка и распознавание фраз не могут быть обработаны одновременно. Если Граммаррекогнизер или Кэйвордрекогнизер активен, Диктатионрекогнизер не может быть активным и наоборот.

## <a name="enabling-the-capability-for-voice"></a>Включение возможности для голоса

Для использования речевого ввода приложение должно быть объявлено с помощью функции **микрофона** .
1. В редакторе Unity выберите **правка > параметры проекта > проигрыватель** .
2. Выберите вкладку " **Магазин Windows** "
3. В разделе " **Параметры публикации > возможности** " проверьте возможность использования **микрофона** .
4. Предоставление разрешений приложению доступа к микрофону на устройстве HoloLens
    * Вам будет предложено сделать это при запуске устройства, но если вы случайно щелкнули "нет", вы можете изменить разрешения в параметрах устройства.

## <a name="phrase-recognition"></a>Распознавание фраз

Чтобы разрешить приложению прослушивать определенные фразы, произносимые пользователем, выполните некоторые действия:
1. Укажите, какие фразы следует прослушивать с помощью `KeywordRecognizer` или `GrammarRecognizer`
2. Обрабатывает `OnPhraseRecognized` событие и принимает действие, соответствующее распознанной фразе

### <a name="keywordrecognizer"></a>кэйвордрекогнизер

**Пространство имен:** *UnityEngine. Windows. Speech*<br>
**Типы:** *кэйвордрекогнизер*, *фрасерекогнизедевентаргс*, *спичеррор*, *спичсистемстатус*

Чтобы сохранить несколько нажатий клавиш, потребуется несколько операторов using:

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

Затем добавим несколько полей в класс для хранения словаря распознавателя и ключевого слова >.

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

Теперь добавьте в словарь ключевое слово, например в `Start()` методе. В этом примере мы добавляем ключевое слово "Activate":

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

Создайте распознаватель ключевых слов и сообщите ему, что мы хотим узнать:

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

Теперь Зарегистрируйтесь для `OnPhraseRecognized` события

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

Пример обработчика:

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

Наконец, начните распознать!

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a>граммаррекогнизер

**Пространство имен:** *UnityEngine. Windows. Speech*<br>
**Типы**: *граммаррекогнизер*, *фрасерекогнизедевентаргс*, *спичеррор*, *спичсистемстатус*

Граммаррекогнизер используется, если вы указываете грамматику для распознавания с помощью SRGS. Это может быть полезно, если приложение содержит несколько ключевых слов, если вы хотите распознавать более сложные фразы или хотите легко включать и выключать наборы команд. Сведения о формате файла см. [в статье Создание грамматик с помощью XML-кода SRGS](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) .

После того как грамматика SRGS будет доступна в проекте в [папке стреамингассетс](https://docs.unity3d.com/Manual/StreamingAssets.html):

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

Создайте `GrammarRecognizer` и передайте ему путь к файлу SRGS:

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

Теперь Зарегистрируйтесь для `OnPhraseRecognized` события

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

Вы получите обратный вызов, содержащий сведения, указанные в грамматике SRGS, которую можно правильно обойти. Большая часть важной информации будет предоставлена в `semanticMeanings` массиве.

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

Наконец, начните распознать!

```
grammarRecognizer.Start();
```

## <a name="dictation"></a>Диктовка

**Пространство имен:** *UnityEngine. Windows. Speech*<br>
**Типы**: *диктатионрекогнизер*, *спичеррор*, *спичсистемстатус*

Используйте `DictationRecognizer` для преобразования речи пользователя в текст. Диктатионрекогнизер предоставляет функции [диктовки](../../design/voice-input.md#dictation) и поддерживает регистрацию и прослушивание событий завершения и фразы, поэтому вы можете отправить отзыв пользователю, когда они говорят и затем. `Start()` методы и, `Stop()` соответственно, включают и отключают распознавание диктовки. После завершения с распознавателем его следует удалить с помощью, `Dispose()` чтобы освободить используемые ресурсы. Он автоматически освобождает эти ресурсы во время сборки мусора при дополнительных затратах на производительность, если они не выявляются до этого.

Чтобы начать работу с диктовкой, необходимо выполнить несколько шагов.
1. Создать новый `DictationRecognizer`
2. Обработку событий диктовки
3. Запуск Диктатионрекогнизер

### <a name="enabling-the-capability-for-dictation"></a>Включение функции для диктовки

Для использования режима диктовки в приложении необходимо объявить **клиент Интернета** и возможности **микрофона** .
1. В редакторе Unity выберите **правка > параметры проекта > проигрыватель** .
2. Выберите на вкладке " **Магазин Windows** "
3. В разделе " **Параметры публикации > возможности** " проверьте возможность **InternetClient**
    * Кроме того, если микрофон еще не включен, проверьте возможность использования **микрофона** .
4. Предоставьте доступ к приложению для доступа к микрофону на устройстве HoloLens, если вы еще этого не сделали.
    * Вам будет предложено сделать это при запуске устройства, но если вы случайно щелкнули "нет", вы можете изменить разрешения в параметрах устройства.

### <a name="dictationrecognizer"></a>диктатионрекогнизер

Создайте Диктатионрекогнизер следующим образом:

```
dictationRecognizer = new DictationRecognizer();
```

Существует четыре события диктовки, которые можно подписывать и обрабатывать для реализации поведения диктовки.
1. `DictationResult`
2. `DictationComplete`
3. `DictationHypothesis`
4. `DictationError`

**диктатионресулт**

Это событие возникает после приостановки пользователем, как правило, в конце предложения. Здесь возвращается полная распознанная строка.

Сначала Подпишитесь на `DictationResult` событие:

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

Затем обработайте обратный вызов Диктатионресулт:

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

**диктатионхипосесис**

Это событие возникает постоянно во время разговора пользователя. Как распознаватель прослушивает этот момент, он предоставляет текст о том, что он слышал.

Сначала Подпишитесь на `DictationHypothesis` событие:

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

Затем обработайте обратный вызов Диктатионхипосесис:

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

**диктатионкомплете**

Это событие возникает при остановке распознавателя, при вызове из метода Stop (), истечения времени ожидания или при возникновении какой-либо другой ошибки.

Сначала Подпишитесь на `DictationComplete` событие:

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

Затем обработайте обратный вызов Диктатионкомплете:

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

**диктатионеррор**

Это событие возникает при возникновении ошибки.

Сначала Подпишитесь на `DictationError` событие:

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

Затем обработайте обратный вызов Диктатионеррор:

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

После подписки и обработки событий диктовки запустите распознаватель диктовки, чтобы начать получать события.

```
dictationRecognizer.Start();
```

Если вы больше не хотите поддерживать Диктатионрекогнизер, необходимо отменить подписывание событий и ликвидировать Диктатионрекогнизер.

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**Советы**
* `Start()` методы и, `Stop()` соответственно, включают и отключают распознавание диктовки.
* После завершения с распознавателем его необходимо удалить с помощью, `Dispose()` чтобы освободить используемые ресурсы. Он автоматически освобождает эти ресурсы во время сборки мусора при дополнительных затратах на производительность, если они не выявляются до этого.
* Время ожидания происходит по истечении заданного периода времени. Эти времена ожидания можно проверить в `DictationComplete` событии. Существует два времени ожидания, которые следует учитывать:
   1. Если распознаватель запускается и не слышит звук в течение первых пяти секунд, время ожидания истекает.
   2. Если распознаватель предоставил результат, а затем слышит бездействия в течение 20 секунд, время ожидания истечет.

## <a name="using-both-phrase-recognition-and-dictation"></a>Использование распознавания и диктовки фраз

Если вы хотите использовать как распознавание, так и диктовку в приложении, необходимо полностью закрыть один из них, прежде чем можно будет начать другой. Если вы используете несколько Кэйвордрекогнизерс, вы можете завершить их все одновременно с помощью:

```
PhraseRecognitionSystem.Shutdown();
```

Можно вызвать `Restart()` для восстановления всех распознавателей до их предыдущего состояния после остановки диктатионрекогнизер:

```
PhraseRecognitionSystem.Restart();
```

Кроме того, можно просто запустить Кэйвордрекогнизер, который также перезапустит Фрасерекогнитионсистем.

## <a name="voice-input-in-mixed-reality-toolkit"></a>Речевой ввод в наборе средств Mixed Reality

Примеры МРТК для речевого ввода можно найти в следующих демонстрационных сценах:
* [Диктовка](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Dictation)
* [Речь](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Speech)

## <a name="next-development-checkpoint"></a>Следующий этап разработки

Если вы используете точку контрольной точки разработки Unity, которую мы собрали, то вам следует ознакомиться с возможностями и API платформы смешанной реальности:

> [!div class="nextstepaction"]
> [общие возможности](shared-experiences-in-unity.md);

Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#2-core-building-blocks).